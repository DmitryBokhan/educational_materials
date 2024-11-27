Больше инф. тут:
https://gist.github.com/vanushwashere/6f255caf4fa42673153db035222701f2


Конфигурационный файл:
`/etc/systemd/system/supervisord.service`

Остановка:
````
sudo systemctl daemon-reload
sudo systemctl enable supervisord
````

Запуск:
``
sudo systemctl start supervisord
``

Провека статуса:
``
sudo systemctl status supervisord
``