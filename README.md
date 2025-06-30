# Лаб 8. Приложение и CI/CD-пайплайн

## Описание Задания

Требуется Cloud-native приложение и CI/CD окружение к нему:

1. Создаем само приложение

2. Создаем юнит тесты для приложения

3. Докеризируем: Создаем докерфайл для сборки контейнера

4. Описываем CI-сценарии для Github Actions производящие lint, unit-test, build-test

5. Куберизируем: Создаем манифесты для запуска приложения и сервисов в кластере

6. Описываем CD-сценарии для Github Actions производящие docker build и push в Docker Hub

7. Устанавливаем ArgoCD и подключаем к GitHub

8. Проверяем весь CI/CD workflow в сборе

### Запуск ArgoCD
```bash
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "LoadBalancer"}}'
kubectl patch svc argocd-server -n argocd -p '{"spec": {"externalIPs": [ "192.168.1.229" ]}}'
 
 
kubectl -n argocd get secret argocd-initial-admin-secret --template={{.data.password}} | base64 -d
```

### Пример работы
1. Работа AgroCD
![Снимок экрана от 2025-06-30 19-56-41](https://github.com/user-attachments/assets/dd6c26c9-c203-4782-934f-4e19edb4eef4)

2. Обновление `ROLLING-UPDATE` AgroCD
![Снимок экрана от 2025-06-30 19-56-59](https://github.com/user-attachments/assets/b87cc98c-15bc-4fad-af8f-ddcfaeac0d41)

3. Работа приложения после деплоя
![Снимок экрана от 2025-06-30 20-05-33](https://github.com/user-attachments/assets/1aab6dfe-88f9-428c-b669-2609bd7a0e37)
