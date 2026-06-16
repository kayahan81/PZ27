---
# Практическое задание 27

## ЭФМО-02-25 

## Алиев Каяхан Командар оглы
---
# Тема работы
Создание GraphQL API с использованием gqlgen. Запросы и мутации

## Цели занятия
Научиться проектировать GraphQL-схему, генерировать серверный каркас gqlgen и реализовывать резолверы для запросов (Query) и изменений (Mutation).


## Коды статуса:
-	200 OK — успешный ответ
-	201 Created — ресурс создан
-	204 No Content — успешно, без тела
-	400 Bad Request — неверные данные
-	404 Not Found — ресурс не найден
-	422 Unprocessable Entity — некорректные данные по смыслу
-	500 Internal Server Error — внутренняя ошибка

# Примечания по конфигурации и требования

Для запуска требуется:

Go: версия 1.25.1

<img width="841" height="232" alt="Установка Git и Go" src="https://github.com/user-attachments/assets/8e01d831-5a7f-4376-8348-9052b240aec9" />


# Команды запуска/сборки
## 1) Клонировать данный репозиторий в удобную для вас папку:
```Powershell
git clone https://github.com/kayahan81/pz27
```
## 2) Перейти в папку pz19:
```Powershell
cd pz27/services/graphql
```
## 3) Загрузка зависимостей:
```Powershell
go mod tidy
```
## 4) Команда запуска
В первом окне
```Powershell
go run github.com/99designs/gqlgen generate
$env:GRAPHQL_PORT="8090"
$env:DB_HOST="localhost"
$env:DB_PORT="5432"
$env:DB_USER="tasks_user"
$env:DB_PASSWORD="tasks_pass"
$env:DB_NAME="tasks_db"
go run ./cmd/graphql
```

# Проверка работоспособности
## Запрос списка задач
```graphql
query {
  tasks {
    id
    title
    description
    done
  }
}
```
## Запрос одной задачи
```graphql
query GetTask($id: ID!) {
  task(id: $id) {
    id
    title
    description
    done
  }
}
```
