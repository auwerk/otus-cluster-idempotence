# ДЗ: идемпотентность API

## Настройка /etc/hosts

Добавить записи:
- 127.0.0.1 arch.homework

## Разворачивание кластера

- Создание пространств имён
```shell
kubectl apply -f ./namespaces.yaml
```

- Установка nginx-ingress-controller
```shell
helm install nginx-ingress ingress-nginx/ingress-nginx --namespace nginx-ic
```

- Установка PostgreSQL для сервиса
```shell
kubectl apply -f ./db/resources.yaml
helm install postgresql -f ./db/postgresql-values.yaml bitnami/postgresql --namespace otus-order
```

- Установка сервиса
```shell
kubectl apply -f ./service-order/resources.yaml
kubectl apply -f ./service-order/ingress.yaml
```

## Тесты Postman/Newman

В файле Otus Idempotence.postman_collection.json