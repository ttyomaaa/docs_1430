Файловая структура новых модулей бота выглядит следующим образом:<br>

:fontawesome-regular-folder: app _**- папка с базой данных и сервисами **_<br> 
&emsp;&emsp;:fontawesome-regular-folder: models _**- модели БД **_  <br>
&emsp;&emsp;:fontawesome-regular-folder: repositories _**- репозиторий БД **_  <br>
...<br>
:fontawesome-regular-folder: db _**- конфигурация SQLAlchemy **_<br> 
&emsp;&emsp;:fontawesome-regular-folder: utils _**- url для подключения к БД **_  <br>
:fontawesome-regular-folder: handlers _**- хендеры бота, в т.ч. новые **_<br>
├── ... <br>
├──:fontawesome-brands-python: form_handlers.py _**- хендлеры опросов **_<br>
└──:fontawesome-brands-python: user_handlers.py _**- хендлер раздела статистики **_<br>
...<br>
:fontawesome-regular-folder: resources _**- медиа-файлы для тестов **_<br> 
...<br>
:fontawesome-regular-folder: templates _**- html страницы для админ-панели **_<br>
├──:fontawesome-solid-file: basic.html _**- базовая страница **_<br>
└──:fontawesome-solid-file: index.html _**- страница после авторизации **_<br>
:fontawesome-brands-python: create_tables.py _**- создание таблиц в БД **_<br> 
:fontawesome-brands-python:  init_tables.py _**- заполнение таблиц в БД **_<br> 
:fontawesome-brands-python:  login.py _**- аутентификация на сайте **_<br> 
:fontawesome-brands-python:  main.py _**- запуск бота и веб-приложения **_ <br>
:fontawesome-solid-file: requirements.txt _**- файл списка необходимых библиотек **_  <br>
:fontawesome-brands-python:  settings.py _**- конфигурация БД и бота **_ <br>
:fontawesome-brands-python:  stats.py _**- генерация картинок статистики **_ <br>
:fontawesome-brands-python:  utils.py _**- сервисы отчета по пользователю **_ <br>
