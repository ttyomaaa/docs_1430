## Запуск и подключение модулей
Инициализация и конфигурация диспетчера и бота описаны в файле :fontawesome-brands-python: _settings.py_ <br>
Запуск бота, а так же покдючение всех обработчиков через роутеры осуществляется в файле :fontawesome-brands-python: _bot.py_ <br>
<br>
Иерархия роутеров отображена на следующей диаграмме:
``` mermaid
graph LR
  A[Telegram] --->|Апдейт| B[Диспетчер];
  B --->|Не обработано| C[coder.py];
  B --->|Обработано| A;
  C --->|Не обработано| D[structure.py];
  C --->|Обработано| A;
  D --->|Не обработано| E[commands.py];
  D --->|Обработано| A;
  E --->|Обработано| A;
```
## Обработка различных сценариев взаимодействия
### Команды пользователя
Обработка первых этапов взаимодействия пользователя с ботом описана в файле <br>
:fontawesome-brands-python: _commands.py_ <br>

* К примеру, данный хендлер реагирует на команду _/chapters_ :
```py
@router.message(Command('chapters'))
async def command_chapters(message: Message, state: FSMContext):
```
### Работа с первыми инлайн-клавиатурами
После выбора главы взаимодействия обрабатываются в файле :fontawesome-brands-python: _structure.py_ <br>

* К примеру, данный хендлер реагирует на выбор главы :
```py
@router.callback_query(F.data.startswith('chapters'))
async def process_chapters(callback: CallbackQuery, state: FSMContext):
```

* Данный хендлер реагирует на выбор шифра :
```py
@router.callback_query(F.data.startswith('ciphers'), StateFilter(PreButtonStates.chapter_selected))
async def process_ciphers(callback: CallbackQuery, state: FSMContext):
```

* Данный хендлер реагирует на выбор режима(зашифровать/расшифровать) :
```py
@router.callback_query(F.data.startswith('buttons'), StateFilter(PreButtonStates.cipher_selected))
async def process_buttons(callback: CallbackQuery, state: FSMContext):
```
### Работа с режимом шифрования или расшифрования
После выбора шифра и режима работы взаимодействия обрабатываются в файле <br>
:fontawesome-brands-python: _coder.py_ <br>

* Все действия пользователя в одном из режимов обрабатываются в этом хендлере:
```py
@router.message(or_f(StateFilter(ButtonsStates.button1), StateFilter(ButtonsStates.button2)))
async def process_encode_decode(message: Message, state: FSMContext):
```
* Исключение: шифр **Квадрат Полибия**, при расшифровании обрабатывается _частично_ в следующих хенделерах:
```py
@router.callback_query(StateFilter(ButtonsStates.button2), F.data.startswith('bn'))
async def process_matrix(callback: CallbackQuery, state: FSMContext):
```
```py
@router.callback_query(StateFilter(ButtonsStates.button2), F.data.startswith('end'))
async def process_end(callback: CallbackQuery, state: FSMContext):
```
### Подпрограммы шифров и валидаторов
К файлу :fontawesome-brands-python: _coder.py_ в формате python-пакетов подключаются следующие файлы:<br>
1. :fontawesome-brands-python: _cipher.py_ <br>
2. :fontawesome-brands-python: _validators.py_ <br>

* Первый содержит подпрограммы работы шифров, например, четверты шифр второй главы:
```py
def cipher24(input_text: str, first: str, mode: bool, second: str):
```
* Второй содержит валидаторы для ключей шифров, например, валидатор ключа первого шифра четвертой главы:
```py
def key_validation41(key_alpha: str):
```

Бот чувствителен к колчиеству аргументов подпрограмм шифров, на этом строится часть логики работы хендлера:
```py
cipher = getattr(ciphers.cipher, "cipher"+str(chapter_n)+str(cipher_n))

sig = signature(cipher)
params = len(sig.parameters) - 1
if params > 1:
        valid = getattr(filters.validators, "key_validation" + str(chapter_n) + str(cipher_n))
 if params > 2:
        valid2 = getattr(filters.validators, "key_validation" + str(chapter_n) + str(cipher_n) + "_2")
```
### Функция обработки возврата на предыдущий этап
Функция универсальна для любого сценария, при выполнении перемещает пользователя на шаг назад
```py
@router.callback_query(F.data == 'back')
async def go_back(callback: CallbackQuery, state: FSMContext):
```
