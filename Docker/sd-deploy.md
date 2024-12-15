## Install Service Desk on Ubuntu 24.04 LTS
### Устанавливаем Docker 
- https://docs.docker.com/engine/install/ubuntu/
#### 1. Set up Docker's apt repository.
```bash
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

#### 2. Install the Docker packages
```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

#### 3. Verify that the installation is successful by running the `hello-world` image:
```bash
sudo docker run hello-world
```

### Развертывание проекта SD из репозитория Git
 - переходим в каталог
```bash
cd /var/www
```
- клонируем проект SD в папку (например: api-sd.mysite.ru)
- добавляем файл `.env` и устанавливаем пароль для базы данных
- дать разрешение на папку (api-sd.mysite.ru - заменить на свою директорию):
```
sudo chown -R www-data:www-data /var/www/api-sd.mysite.ru/storage
sudo chmod -R 775 /var/www/api-sd.mysite.ru/storage
```

### Запуск Docker контейнера
- переходим в каталог проекта (например api-sd.mysite.ru)
```bash
cd /var/www/api-sd.mysite.ru 
```
- запускаем Docker
```bash
docker compose up -d
```
- выводим список запущенных контейнеров 
```bash
docker ps
```
- переходим в контейнер с проектом и выполняем миграции
```bash
docker exec -it sd_app bash
php artisan migrate
```

