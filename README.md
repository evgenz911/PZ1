# HelloAPI

Простой HTTP-сервис на Go без внешних фреймворков (только стандартная библиотека + `github.com/google/uuid`).

## Структура

```
.
├── go.mod
├── go.sum
└── cmd/
    └── server/
        └── main.go      # точка входа, маршрутизация и обработчики
```

## Запуск

```bash
go run ./cmd/server
```

Сервер слушает порт из переменной окружения `APP_PORT`, по умолчанию `8080`.

## Сборка

Собрать исполняемый файл в локальную папку `bin/`:

```bash
mkdir -p bin
go build -o bin/helloapi ./cmd/server
```

Запустить собранное приложение:

```bash
./bin/helloapi
```

## Эндпоинты

| Метод | Путь     | Описание                          | Формат ответа |
|-------|----------|-----------------------------------|---------------|
| GET   | `/hello` | Приветствие                      | text/plain    |
| GET   | `/user`  | Данные пользователя с UUID       | application/json |
| GET   | `/health`| Проверка работоспособности       | application/json |

### Примеры запросов

```bash
curl http://localhost:8080/hello
curl http://localhost:8080/user
curl http://localhost:8080/health
```

## Зависимости

- [Go](https://go.dev/) ≥ 1.21
- [`github.com/google/uuid`](https://pkg.go.dev/github.com/google/uuid) — генерация UUID

Установка зависимостей:

```bash
go mod tidy
```