### Курс по Docker
https://www.youtube.com/watch?v=O8N1lvkIjig&t=95s


#### создать пользователя-
- `useradd -m -s /bin/bash username`

#### добавить пользователя в группу docker
- `usermo -aG docker username`

#### посмотреть группы пользователя
- `id username`



### Основные команды Docker

Статус докера (процесса)
````
service docker status
````
---
Тестовый образ
````
docker run hello-world
````
---
Посмотреть список контейнеров

- `docker ps`    - запущенные
- `docker ps -a` - остановленные
- `docker ps -l` - ?
---
Удалить контейнер
````
docker rm [IMAGE ID либо NAME контейнера]
````
---
Список images 
````
docker images
````
Удалить image
````
docker rmi [IMAGE ID]
````
---
Удалить всё!
- сначала останавливаем все контейнеры!
- `docker system prune -a --volumes`
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
Паузировать контейнер
- `docker pause [CONTAINER ID либо NAME]`
- `docker ps` - смотрим STAUS, там будет Paused
- что бы снять пауза: `docker unpause [CONTAINER ID либо NAME]`
---
Остановить контейнер
- `docker stop [CONTAINER ID либо NAME]`
---
Убить процесс
- `docker kill [CONTAINER ID либо NAME]`
---
Ключи:
- `-d`   - запустить контейнер в фоновом режиме (detach mode)
- `--rm` - после остановки контейнера он автоматически удаляется 
- `--name` - позволяет задать имя контейнеру
-  Пример: `docker run -d --rm --name My-container ubuntu:20.04`
---
Инспектировать контейнер. Это позволяет получить подробную информацию о контейнере
- `docker inspect [CONTAINER ID либо NAME]`
---
Инспекция потребления ресурсов контейнера
- `docker stats [CONTAINER ID либо NAME]`
````
CONTAINER ID   NAME            CPU %     MEM USAGE / LIMIT     MEM %     NET I/O           BLOCK I/O     PIDS
9879862b151d   project_nginx   0.00%     5.762MiB / 1.925GiB   0.29%     7.95MB / 10.4MB   32.8kB / 0B   4
````
---
Просмотр логов контейнера 
- `docker logs [CONTAINER ID либо NAME]`
- `docker logs -f [CONTAINER ID либо NAME]` - логи в режиме реального времени
---
ЗАЙТИ В КОНТЕЙНЕР!
- `docker exec -it [CONTAINER ID либо NAME] /bin/bash` 
- `docker exec -it [CONTAINER ID либо NAME] bash` - можно и так
---
