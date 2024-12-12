- перезапуск 
````bash
sudo systemctl restart apache2
````
- остановка
````bash
sudo systemctl stop apache2
````
- старт
````bash
sudo systemctl start apache2
````


- Проверьте, что модули SSL и Proxy включены:
````
sudo a2enmod ssl
sudo a2enmod proxy
sudo a2enmod proxy_http
sudo a2enmod proxy_ftp
sudo a2enmod proxy_balancer
sudo a2enmod ssl
sudo systemctl restart apache2
````


Так можно развернуть контейнер на машине где уже есть сайт и работает Apache. Для работы докера настраиваем проксироване на нестандартные порты.
В примере контейнер использует внешние порты 8080 и 8443.  
- Пример для конфигурационного файла Apache `/etc/apache2/sites-available/api-sd.bakra-auto.ru.conf`
````
<VirtualHost *:80>
    ServerName api-sd.bakra-auto.ru

    ProxyPreserveHost On
    ProxyPass / http://127.0.0.1:8080/
    ProxyPassReverse / http://127.0.0.1:8080/

    ErrorLog ${APACHE_LOG_DIR}/api-sd.bakra-auto.ru.error.log
    CustomLog ${APACHE_LOG_DIR}/api-sd.bakra-auto.ru.access.log combined

    # Редирект HTTP на HTTPS
    Redirect permanent / https://api-sd.bakra-auto.ru/
</VirtualHost>

<IfModule mod_ssl.c>
    <VirtualHost *:443>
        ServerName api-sd.bakra-auto.ru

        SSLProxyEngine On
        ProxyPreserveHost On
        ProxyPass / https://127.0.0.1:8443/
        ProxyPassReverse / https://127.0.0.1:8443/

        SSLEngine on
        SSLCertificateFile      /home/ssk/bakra-ssl/bakra.crt
        SSLCertificateKeyFile   /home/ssk/bakra-ssl/bakra.key

        ErrorLog ${APACHE_LOG_DIR}/api-sd.bakra-auto.ru.ssl.error.log
        CustomLog ${APACHE_LOG_DIR}/api-sd.bakra-auto.ru.ssl.access.log combined
    </VirtualHost>
</IfModule>
````
