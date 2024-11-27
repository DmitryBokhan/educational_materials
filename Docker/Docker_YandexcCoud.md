1. Yandex Cloud - арендовать VM c Ubuntu 20.04
2. Установить PHP and Composer:

`sudo apt update`

-------------------------------
Установка PHP 8.0 или 8.1:

Добавьте репозиторий:
````
sudo add-apt-repository ppa:ondrej/php
sudo apt update
````

Установите нужную версию PHP:
````
sudo apt install php8.1
````
---
Установка Composer:

Загрузите установочный скрипт Composer:

`curl -sS https://getcomposer.org/installer | php`

Переместите исполняемый файл Composer в глобальное расположение:
sudo mv composer.phar /usr/local/bin/composer

Проверьте установку Composer:
composer -v

3. Устанавливаем Docker и Docker Compose

https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-20-04-ru

https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-compose-on-ubuntu-20-04-ru

4. Под пользователем root генерируем ssh-key
   ssh-keygen

5. Добавляем ssh-key в GitHub
   Settings->SSH and GPG keys

6. Клонируем проект с GitHub в /var/www/[название папки с проектом]

7. Запускаем проект в Docker
   docker-compose -f docker-compose.prod.yml up -d 