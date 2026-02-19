# Local-Base-

Небольшой локальный проект на Docker Compose:
- `nginx` отдает веб-страницу,
- `postgres` хранит данные,
- `prometheus + grafana` показывают метрики и алерты.

## Что здесь уже есть

### Веб-страница

Стартовая страница открывается по адресу `http://localhost:8080`.

На странице есть:
- вход,
- переключение на регистрацию,
- регистрация с полями: имя, телефон, email, пароль,
- проверка на дубликат: если email или телефон уже заняты, показывается ошибка.

Файл страницы: `web/index.html`.

### База данных

Используется PostgreSQL с такими параметрами:
- `POSTGRES_DB=app_db`
- `POSTGRES_USER=app_user`
- `POSTGRES_PASSWORD=app_password`

## Быстрый старт

Требования:
- установлен Docker с Docker Compose,
- свободные порты: `8080`, `9090`, `3000`.

Запуск:

```bash
docker compose up -d
```

Проверить, что всё поднялось:

```bash
docker compose ps
```

Остановить проект:

```bash
docker compose down
```

## Куда заходить после запуска

- Приложение: `http://localhost:8080`
- Prometheus: `http://localhost:9090`
- Grafana: `http://localhost:3000`

Логин/пароль Grafana по умолчанию:
- `admin`
- `admin`

## Мониторинг простыми словами

- `Prometheus` собирает метрики.
- `Grafana` рисует графики на основе этих метрик.
- `postgres-exporter` отдает метрики PostgreSQL.
- `nginx-exporter` отдает метрики Nginx.

Datasource `Prometheus` в Grafana подключается автоматически.

Автоматически загружаются дашборды:
- `Nginx Overview`
- `PostgreSQL Overview`

## Алерты

В Prometheus уже добавлены базовые алерты:
- `PostgresExporterDown`
- `NginxExporterDown`
- `PrometheusTargetDown`
- `PostgresTooManyConnections`

Посмотреть их можно здесь:
- `http://localhost:9090/alerts`

## Где лежат конфиги

- `docker-compose.yml`
- `nginx/nginx.conf`
- `prometheus/prometheus.yml`
- `prometheus/alerts.yml`
- `grafana/provisioning/datasources/datasource.yml`
- `grafana/provisioning/dashboards/dashboards.yml`
- `grafana/dashboards/*.json`
