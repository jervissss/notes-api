# Практическое задание №11: Проектирование REST API (CRUD для заметок)
## Группа: ЭФМО-02-25
## ФИО: Евдоков Богдан Вадимович
## 🎯 Цель работы
Освоить принципы проектирования REST API и разработки структуры backend-приложения на Go. Реализовать CRUD-интерфейс для сущности "Заметка" с применением слоистой архитектуры.

## 📋 Предварительные требования
* Go (версия 1.20 или выше)

* Git for Windows

* PowerShell (встроен в Windows)

## 🚀 Инструкция по запуску на Windows
1. Клонирование репозитория
```powershell
git clone <ваш-репозиторий>
cd notes-api
```
2. Установка зависимостей
```powershell
go mod download
```
3. Запуск Go-сервера
```powershell
go run .\cmd\api\main.go
```
4. Проверка работы API
Создание заметки

```powershell
$body = @{
    title = "Первая заметка"
    content = "Привет, REST API!"
} | ConvertTo-Json -Compress

Invoke-RestMethod -Uri "http://localhost:8080/api/v1/notes" `
    -Method Post `
    -ContentType "application/json" `
    -Body $body
```
Получение списка всех заметок

```powershell
Invoke-RestMethod -Uri "http://localhost:8080/api/v1/notes"
```
Получение заметки по ID

```powershell
Invoke-RestMethod -Uri "http://localhost:8080/api/v1/notes/1"
```
Обновление заметки (частичное)

```powershell
$body = @{
    content = "Обновленный текст заметки"
} | ConvertTo-Json -Compress

Invoke-RestMethod -Uri "http://localhost:8080/api/v1/notes/1" `
    -Method Patch `
    -ContentType "application/json" `
    -Body $body
```
Удаление заметки

```powershell
Invoke-RestMethod -Uri "http://localhost:8080/api/v1/notes/1" `
    -Method Delete
```
## 📁 Структура проекта

<img width="414" height="536" alt="image" src="https://github.com/user-attachments/assets/ba96878f-c04d-40b1-a5f4-527459cbf86e" />


## 📊 Формат данных
Пример JSON для создания заметки:

```json
{
    "title": "Заголовок заметки",
    "content": "Содержимое заметки"
}
```
Пример ответа:

```json
{
    "id": 1,
    "title": "Заголовок заметки",
    "content": "Содержимое заметки",
    "createdAt": "2025-01-15T10:30:00Z",
    "updatedAt": "2025-01-15T10:30:00Z"
}
```
## 📸 Скриншоты работы
Работа API:
<img width="1918" height="1079" alt="Снимок экрана 2025-12-07 190346" src="https://github.com/user-attachments/assets/2f0fc59b-efcc-4828-acca-ca9e91a2951f" />
