### Курс по Docker
https://www.youtube.com/watch?v=O8N1lvkIjig&t=95s


#### создать пользователя-
- `useradd -m -s /bin/bash username`

#### добавить пользователя в группу docker
- `usermo -aG docker username`

#### посмотреть группы пользователя
- `id username`


#### посмотреть список контейнеров
- `docker ps`    - запущенные
- `docker ps -a` - остановленные
- `docker ps -l` - ?


### Основные команды

- статус докера (процесса)
````
service docker status
````

- тестовый образ
````
docker run hello-world
````

- удалить контейнер
````
docker rm [id либо name контейнера]
````

- список images 
````
docker images
````
- удалить image
````
docker rmi [IMAGE ID]
````