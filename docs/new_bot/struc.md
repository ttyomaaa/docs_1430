Файловая структура бота выглядит следующим образом:<br>

:fontawesome-regular-folder: app _**- основная папка с кодом бота**_<br> 
&emsp;&emsp;:fontawesome-regular-folder: ciphers _**- подпрограммы шифров **_  <br>
&emsp;&emsp;└──:fontawesome-brands-python: cipher.py <br>
&emsp;&emsp;:fontawesome-regular-folder: config _**- конфигурации бота **_ <br>
&emsp;&emsp;├──:fontawesome-solid-file: .env _**-  telegram-token **_ <br>
&emsp;&emsp;├──:fontawesome-brands-python: bot_startup.py <br>
&emsp;&emsp;└──:fontawesome-brands-python: settings.py <br>
&emsp;&emsp;:fontawesome-regular-folder: enums _**- конфигурации шифров и выдаваемых сообщений **_ <br>
&emsp;&emsp;├──:fontawesome-brands-python: texts.py <br>
&emsp;&emsp;└──:fontawesome-solid-file: vars_for_enigma.xlsx <br>
&emsp;&emsp;:fontawesome-regular-folder: filters _**- валидаторы для шифров **_ <br> 
&emsp;&emsp;└──:fontawesome-brands-python: validators.py <br>
&emsp;&emsp;:fontawesome-regular-folder: fsm  _**- машина состояний бота **_ <br> 
&emsp;&emsp;└──:fontawesome-brands-python: states.py <br>
&emsp;&emsp;:fontawesome-regular-folder: handlers _**- папка всех обработчиков бота **_ <br>
&emsp;&emsp;├──:fontawesome-brands-python: coder.py <br>
&emsp;&emsp;├──:fontawesome-brands-python: commands.py <br>
&emsp;&emsp;└──:fontawesome-brands-python: structure.py <br>
&emsp;&emsp;:fontawesome-regular-folder: keyboards _**- строители клавиатур бота **_ <br>
&emsp;&emsp;└──:fontawesome-brands-python: keyboard_builders.py <br>
&emsp;&emsp;:fontawesome-regular-folder: resourcesdb  _**- медиа-файлы **_ <br>
&emsp;&emsp;└──:fontawesome-regular-folder: media <br>
&emsp;&emsp;:fontawesome-regular-folder: storage _**- хранилище временных сообщений **_ <br>
&emsp;&emsp;└──:fontawesome-brands-python: custom_storage.py <br>
&emsp;&emsp;:fontawesome-brands-python: bot.py _**- запуск бота и подключение модулей **_ <br>
:fontawesome-regular-folder: tests _**- папка конфигураций и программ тестов **_ <br>
├──:fontawesome-brands-python: \_\_init__.py <br>
├──:fontawesome-brands-python: conftest.py <br>
├──:fontawesome-brands-python: test_errors.py <br>
├──:fontawesome-brands-python: test_logic.py <br>
└──:fontawesome-brands-python: test_unit.py <br>
:fontawesome-solid-file: requirements.txt _**- файл списка необходимых библиотек **_  <br>



