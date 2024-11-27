### Курс по Docker
https://www.youtube.com/watch?v=O8N1lvkIjig&t=95s


#### создать пользователя-
- `useradd -m -s /bin/bash username`

#### добавить пользователя в группу docker
- `usermo -aG docker username`

#### посмотреть группы пользователя
- `id username`



### Основные команды Docker

- статус докера (процесса)
````
service docker status
````

- тестовый образ
````
docker run hello-world
````
---
- посмотреть список контейнеров

- `docker ps`    - запущенные
- `docker ps -a` - остановленные
- `docker ps -l` - ?
- удалить контейнер
````
docker rm [IMAGE ID либо NAME контейнера]
````
---
- список images 
````
docker images
````
- удалить image
````
docker rmi [IMAGE ID]
````
---
- `dockler run [NAME контейнера]` - создать новый контейнер
- `dockler start [IMAGE ID либо NAME контейнера]` - запустит остановленный контейнер
---

Чтобы скачать образ нужной версии с DockerHub нежно это явно указывать:

- `docker run ubuntu:20.04` - так мы скачаем и сразу запустим образ.
- далее можно будет увидеть образ в списке `docker images`
- если при запуске образа не указывать версию, то докер сначала будет пытаться запустить `latest` версию
---

В DockerHub при выборе контейнеров есть:
- `TAG` - версия образа
- `OS/ARCH` - варианты архитектур на которые подходит образ (на обычный сервер подходит amd64, для RasberyPy - arm)
---

