🏗️ Capi Project - Clean Architecture
Микросервис построен по принципам Clean Architecture с четким разделением слоев и зависимостей

📋 Структура проектов
Проект	Назначение	Зависимости
Capi.API	Web API, контроллеры, точка входа	Application, Infrastructure
Capi.Application	Бизнес-логика, сервисы, use cases	Domain
Capi.Domain	Доменные модели, интерфейсы, entities	-
Capi.Infrastructure	Данные, внешние сервисы, repositories	Application
⚡ Быстрая настройка
Добавить все проекты в solution
dotnet sln add src/Services/Capi/**/*.csproj
Или добавить проекты по отдельности
# API-слой (зависит от Application, Infrastructure)
dotnet sln add "src/Services/Capi/Capi.API/Capi.API.csproj"

# Слой приложения (зависит от Domain)
dotnet sln add "src/Services/Capi/Capi.Application/Capi.Application.csproj"

# Доменный слой (без зависимостей)
dotnet sln add "src/Services/Capi/Capi.Domain/Capi.Domain.csproj"

# Инфраструктурный слой (зависит от Application)
dotnet sln add "src/Services/Capi/Capi.Infrastructure/Capi.Infrastructure.csproj"
🚀 Сборка и запуск
# Восстановить зависимости
dotnet restore

# Собрать проект
dotnet build

# Запустить API
dotnet run --project src/Services/Capi/Capi.API
🔍 Проверка настройки
# Просмотреть все проекты в solution
dotnet sln list

# Проверить зависимости проектов
dotnet list src/Services/Capi/Capi.API reference
🎯 Архитектурные принципы
Инверсия зависимостей
Domain не зависит ни от чего.

Разделение ответственности
Каждый слой имеет чёткое назначение, бизнес-логика изолирована от внешних зависимостей.

Расширяемость
Легко добавлять новую функциональность.