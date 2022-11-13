# Домашнее задание к занятию "14.1 Создание и использование секретов"

## Задача 1: Работа с секретами через утилиту kubectl в установленном minikube

Выполните приведённые ниже команды в консоли, получите вывод команд. Сохраните
задачу 1 как справочный материал.

### Как создать секрет?

```
openssl genrsa -out cert.key 4096
openssl req -x509 -new -key cert.key -days 3650 -out cert.crt \
-subj '/C=RU/ST=Moscow/L=Moscow/CN=server.local'
kubectl create secret tls domain-cert --cert=certs/cert.crt --key=certs/cert.key
```

## Ответ: секрет создан:

![image](https://user-images.githubusercontent.com/92969676/201520440-ad42fced-d86f-4d13-b5f4-aa8ac6a818c6.png)



### Как просмотреть список секретов?

```
kubectl get secrets
kubectl get secret
```

## Ответ: 

![image](https://user-images.githubusercontent.com/92969676/201520465-a16ed64b-0fa0-4e86-afad-437459c23626.png)

### Как просмотреть секрет?

```
kubectl get secret domain-cert
kubectl describe secret domain-cert
```

## Ответ: 

![image](https://user-images.githubusercontent.com/92969676/201520495-03ad1109-eacf-4466-b49e-178cf9ce6ce1.png)


### Как получить информацию в формате YAML и/или JSON?

```
kubectl get secret domain-cert -o yaml
kubectl get secret domain-cert -o json
```
## Ответ: 

![image](https://user-images.githubusercontent.com/92969676/201520535-0e322f0a-dcdb-4f9b-bfd9-60b1521c4841.png)

![image](https://user-images.githubusercontent.com/92969676/201520587-180d32bc-eb45-4df8-b361-31e8fe199de3.png)


### Как выгрузить секрет и сохранить его в файл?

```
kubectl get secrets -o json > secrets.json
kubectl get secret domain-cert -o yaml > domain-cert.yml
```
## Ответ json: 

![image](https://user-images.githubusercontent.com/92969676/201520638-0f1a5bfb-74ae-4e7f-99b1-661f3b8ef0d2.png)

![image](https://user-images.githubusercontent.com/92969676/201520690-ad0ad812-a20c-4a6d-88e4-7e5a0c866765.png)

## Ответ yml: 

![image](https://user-images.githubusercontent.com/92969676/201520665-38b53985-8c27-4e7a-9148-0d826bd4dd15.png)

![image](https://user-images.githubusercontent.com/92969676/201520707-2e8001d7-6f10-441a-8943-2121373b96f4.png)

```

### Как удалить секрет?

```
kubectl delete secret domain-cert
```

### Как загрузить секрет из файла?

```
kubectl apply -f domain-cert.yml
```
