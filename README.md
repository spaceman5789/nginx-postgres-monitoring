# Local-Base-

Приложение с веб-сервисом `nginx` и базой данных `PostgreSQL` в Docker Compose.

## Запуск

```bash
docker compose up -d
```

## Остановка

```bash
docker compose down
```

## Проверка сервисов

```bash
docker compose ps
```

`nginx` будет доступен на `http://localhost:8080`.

## Стартовая страница

Добавлена простая HTML-страница входа с переключением на регистрацию.

Регистрация содержит поля:
- имя
- номер телефона
- email
- пароль

Вход выполняется по:
- email + пароль
или
- номеру телефона + пароль

При регистрации есть проверка: если аккаунт с таким email или телефоном уже существует, показывается ошибка

Файл страницы: `web/index.html`.

Параметры БД:
- `POSTGRES_DB=app_db`
- `POSTGRES_USER=app_user`
- `POSTGRES_PASSWORD=app_password`
