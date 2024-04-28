### Здесь про код например:

```py 
class PreButtonStates(StatesGroup):
    chapter_selected = State()
    cipher_selected = State()


class ButtonsStates(StatesGroup):
    button1 = State()
    button2 = State()
```

### Или вот еще

```py
@router.message(Command('chapters'))
async def command_chapters(message: Message, state: FSMContext):
```
