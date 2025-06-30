# situ_devops-lab_08

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

