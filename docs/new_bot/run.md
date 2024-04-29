## Установка требуемых библиотек и настройка окружения

```commandline
$ sudo apt-get install python3.11-venv
$ python3.11 -m venv venv
$ source venv/bin/activate
$ pip install -r requirements.txt
```

## Запуск тестирования

С подсчетом покрытия:
```commandline
$ coverage run --branch -m pytest
$ coverage html
```
Без подсчета покрытия:
```commandline
$ python -m pytest 
```

## Запуск бота

```commandline
$ python3 bot.py > output.log &
```