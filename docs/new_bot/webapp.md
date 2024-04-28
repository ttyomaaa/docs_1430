Все исторические справки и примеры для шифров подключаются к боту через интерфейс Telgram WebApp.

WebApp работает с ссылками на уже готовые веб-приложения. <br> 
Для этих нужд был создан репозиторий на GitHub, содержащий все необходимые html-страницы, всего 55. Далее, с помощью GitHub Pages было осуществлено развертывание на сервере.<br><br>
Ссылка на репозиторий со справками и инструкциями:  :fontawesome-brands-github: [p1430webapp](https://github.com/ttyomaaa/p1430webapp)<br>
<br>
Генерация типовых ссылок и встройка в кнопки клавиатуры Telegram выполняются в следующих функциях:<br>

* Для инлайн-клавиатур
```py
def inline_keyboard_maker_webapp(keyboard_pool: list, identity: str, mode: int, cipher_code: str) \
        -> InlineKeyboardMarkup:
``` 

* Для обычных клавиатур
```py
def reply_keyboard_maker(keyboard_pool: list, cipher_code: str, mode: int) -> ReplyKeyboardMarkup:
```

