# Фудграм

**Фудграм** — сайт, на котором пользователи могут публиковать свои рецепты, добавлять чужие рецепты в избранное и подписываться на публикации других авторов. Зарегистрированным пользователям также доступен сервис **«Список покупок»**, который позволяет создавать список продуктов для покупки, необходимый для приготовления выбранных блюд.

## Запуск проекта

Для запуска проекта требуется установленный **Docker** и **Docker Compose**. 

### Установка Docker

Если у вас ещё не установлен Docker, следуйте инструкциям для вашей операционной системы:

- **[Docker для Windows](https://docs.docker.com/docker-for-windows/install/)**
- **[Docker для macOS](https://docs.docker.com/docker-for-mac/install/)**
- **[Docker для Linux](https://docs.docker.com/engine/install/)**

### Настройка окружения

1. Клонируйте репозиторий проекта:
    ```bash
    git clone https://github.com/SteSha28/foodgram-st.git
    cd foodgram-st
    ```

2. Создайте файл `.env` в корне проекта и добавьте в него следующие переменные окружения:
    ```env
    POSTGRES_USER=django_user
    POSTGRES_PASSWORD=django_password
    POSTGRES_DB=django

    DB_HOST=db
    DB_PORT=5432

    ALLOWED_HOSTS="127.0.0.1 localhost"
    ```

### Сборка и запуск контейнеров

1. Выполните команду для сборки и запуска контейнеров:

    ```bash
    docker compose up --build
    ```
    
2. Выполните миграции:

    ```bash
    docker compose exec backend python manage.py migrate --noinput
    ```
    
3. Выполните сборку статических файлов:

    ```bash
    docker compose exec backend python manage.py collectstatic --no-input
    ```
    
4. Загрузите данные об ингредиентах:

    ```bash
    docker compose exec backend python manage.py import_ingredients
    ```
    
5. При желании загрузите тестовых пользователей:

    ```bash
    docker compose exec backend python manage.py loaddata test_data.json
    ```
    
5. Создайте пользователя:
    ```bash
    docker compose exec backend python manage.py createsuperuser
    ```

6. Когда контейнеры будут запущены, проект будет доступен по следующим адресам:

    - Главная страница: [http://127.0.0.1:8000](http://127.0.0.1:8000)
    - Админ-панель Django: [http://127.0.0.1:8000/admin/](http://127.0.0.1:8000/admin/)
    - Документация API: [http://127.0.0.1:8000/api/docs/](http://127.0.0.1:8000/api/docs/)


