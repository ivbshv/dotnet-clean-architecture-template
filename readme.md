markdown
# dotnet-clean-architecture-template

🏗️ .NET Clean Architecture Template  
Готовый к использованию шаблон для создания микросервисов на .NET с архитектурой Clean Architecture.

Игорь Бушуев 👨‍💻 GitHub: [@ivbshv](https://github.com/ivbshv) 💬 Telegram: [@ivbshv](https://t.me/ivbshv)

---

## 📋 Что создаёт шаблон

При использовании команды `dotnet new Capi -n MyProject` создаётся следующая структура:
MyProject/
├── README.md # Инструкции по проекту
├── MyProject.API/ # Слой Web API
├── MyProject.Application/ # Бизнес-логика
├── MyProject.Domain/ # Доменные модели
└── MyProject.Infrastructure/ # Данные и внешние сервисы



---

## 🚀 Быстрый старт

### Добавить источник GitHub Packages

Создайте Personal Access Token на GitHub с правами `read:packages` и выполните:

```bash
dotnet nuget add source https://nuget.pkg.github.com/ivbshv/index.json \
  --name github-ivbshv \
  --username ivbshv \
  --password <токен> \
  --store-password-in-clear-text
Установить шаблон
bash
dotnet new install ivbshv.cleanarchitecture.template
Использовать шаблон
Создать новый проект:

bash
dotnet new Capi -n MyMicroservice
Перейти в проект и запустить:

bash
cd MyMicroservice
dotnet build
dotnet run --project MyMicroservice.API
🛠️ Управление шаблоном
Действие	Команда
Проверить установку	dotnet new list
Обновить шаблон	dotnet new install ivbshv.cleanarchitecture.template --force
Удалить шаблон	dotnet new uninstall ivbshv.cleanarchitecture.template
Удалить источник	dotnet nuget remove source github-ivbshv
📚 Дополнительные команды
Посмотреть все источники NuGet:

bash
dotnet nuget list source
📦 Публикация новых версий (для автора)
Внесите изменения в шаблон:

Отредактируйте файлы в working/content/Capi/

Обновите PackageVersion в Template.csproj

Закоммитьте и создайте тег:

bash
git add .
git commit -m "Update template: добавлена новая функциональность"
git push origin main

git tag v1.0.0
git push origin v1.0.0
Автоматическая публикация:

GitHub Actions автоматически опубликует пакет в GitHub Packages при создании тега

Проверить публикацию: Actions → статус workflow, Packages → новая версия

🔧 Локальная разработка шаблона
Клонировать репозиторий:

bash
git clone https://github.com/ivbshv/dotnet-clean-architecture-template.git
cd dotnet-clean-architecture-template
Установить локально для тестирования:

bash
cd working
dotnet new install .
Тестировать изменения:

bash
dotnet new Capi -n TestProject
Удалить локальную версию:

bash
dotnet new uninstall "/полный/путь/к/working"
Подготовка
text
dotnet --version 9.0.102
📋 Создание проекта
В папке шаблона (Capi):

bash
dotnet new web -n "Capi.API"
dotnet new classlib -n "Capi.Domain"
dotnet new classlib -n "Capi.Application"
dotnet new classlib -n "Capi.Infrastructure"
В корне репозитория:

bash
dotnet new gitignore
⚒️ Как прописать зависимости
Из проекта Capi.API:

bash
dotnet add reference "../Capi.Application"
dotnet add reference "../Capi.Infrastructure"
Из проекта Capi.Application:

bash
dotnet add reference "../Capi.Domain"
Проект Capi.Domain не имеет внешних зависимостей

Из проекта Capi.Infrastructure:

bash
dotnet add reference "../Capi.Application"
🛠️ Зависимости для функционирования Swagger
Установка библиотеки:

bash
dotnet add package "Swashbuckle.AspNetCore" --version "9.0.3"
Регистрация сервисов:

csharp
builder.Services.AddEndpointsApiExplorer();
builder.Services.AddSwaggerGen();
Конфигурация приложения:

csharp
if (app.Environment.IsDevelopment())
{
    app.UseSwagger();
    app.UseSwaggerUI();
}
Для использования IServiceCollection:

bash
dotnet add package "Microsoft.Extensions.DependencyInjection.Abstractions" --version "9.0.7"
Для использования IConfiguration:

bash
dotnet add package "Microsoft.Extensions.Configuration" --version "9.0.7"
