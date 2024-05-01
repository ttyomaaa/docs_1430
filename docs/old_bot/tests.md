## Начало взаимодействия
После нажатия на кнопку "пройти тест" активируется следующий хендлер:
```py
@router.callback_query(F.data == 'form', ~StateFilter(FSMReadSolve.solve_task))
async def process_form(callback: CallbackQuery, state: FSMContext):
```
В нем подготавливаются состояние и данные, а так же сохраняется номер главы.

За сообщения, высылаемые пользователю по ходу всего опроса, отвечает следующая функция:
```py
async def send_test(form, current_id, message):
```

## Цикл опроса
Здесь работает следующий хендлер:
```py
@router.message(StateFilter(FSMReadSolve.form))
async def process_form(message: Message, state: FSMContext):
```
Он так же вызывает дополнительные функции для проверки ответов, (возможно, досрочного) завершения опроса, получения оценки.
В нем же вызываются сервисы БД, для записи формы с результатами по завершении процедуры.

## Статистика
За статистику в боте отвечает этот хендлер:
```py
@router.message(Command(commands=['stats']), ~StateFilter(FSMReadSolve.solve_task))
async def process_stats(message: Message, state: FSMContext):
```
В нем используется сервис БД для получения отчета по запросившему пользователю и функция `#!python get_stats()`, для создания графика статистики по всем отчетам.