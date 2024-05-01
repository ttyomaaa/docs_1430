## Инициализация базы данных:
```commandline
sudo -i -u postgres
psql
postgres=# CREATE USER <из файла конфигурации> PASSWORD '<из файла конфигурации>';
postgres=# CREATE DATABASE <из файла конфигурации> OWNER <из файла конфигурации>;
postgres=# \q
exit
```
## Создание и заполнение таблиц:
```commandline
python3 create_tables.py
python3 init_tables.py
```
## Запуск бота:
```commandline
python3 main.py > output.log &
```
## Запуск веб-приложения:
```commandline
sudo systemctl start nginx
sudo systemctl reload nginx
sudo systemctl daemon-reload
sudo systemctl start fastapp
```
