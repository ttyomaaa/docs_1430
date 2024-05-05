Используемый фреймворк - **FastAPI**

## GET-запросы
* Базовая html-страница (без авторизации): <br>
```py
@app.get("/results/", response_class=HTMLResponse)
async def results(request: Request):
```

* Продвинутая html-страница (доступна после авторизации): <br>
```py
@app.get("/admin", response_class=HTMLResponse)
async def process_admin(username: Annotated[str, Depends(get_current_username)], request: Request):
```

## POST-запросы
* Логин на сайте: <br>
```py
@app.post("/results/login")
async def process_login():
```

* Отчет по пользователю: <br>
```py
@app.post("/tguser/")
async def process_user(request: Request):
```

* Публикация: <br>
```py
@app.post("/publication/")
async def process_publication(request: Request):
```

## Аутентификация
HTTP Basic, введенная связка логин-пароль передается на сервер, где байтово безопасно сравнивает полученные значения с истинными, исключая атаку по времени. <br>
В случае несовпадения доступ к продвинутой html-странице блокируется: <br>
```py
        raise HTTPException(
            status_code=status.HTTP_401_UNAUTHORIZED,
            detail="Incorrect user or password",
            headers={"WWW-Authenticate": "Basic"},
        )
```
