# Инструкции по запуску фронтенда, бэкенда и PostgreSQL

## 1. Клонирование репозитория

```bash
git https://github.com/Termolk/IT-LearnHub.git
cd IT-LearnHub
```

## 2. Запуск только PostgreSQL

Для того чтобы запустить только PostgreSQL, выполните следующие шаги:

1. Перейдите в корневую директорию проекта, где находится файл `docker-compose.yml`.

2. Запустите контейнер с PostgreSQL:
   ```bash
   docker-compose up -d db
   ```

3. Проверьте, что PostgreSQL запущен и доступен на порту 5432.

## 3. Запуск бэкенда и применение миграций

Теперь, когда PostgreSQL запущен, можно запустить бэкенд и применить миграции:

1. Перейдите в директорию с бэкендом:
   ```bash
   cd backend
   ```

2. Убедитесь, что у вас установлены все зависимости:
   ```bash
   pip install -r requirements.txt
   ```

3. Примените миграции базы данных:
   ```bash
   python manage.py migrate
   ```
   
4.  Создайте суперпользователя:
   ```bash
  python manage.py createsuperuser
  ```

5. Запустите сервер разработки:
   ```bash
   python manage.py runserver 0.0.0.0:8000
   ```

6. Бэкенд будет доступен по адресу [http://localhost:8000](http://localhost:8000).
6. Админ панель будет доступен по адресу [http://localhost:8000/admin](http://localhost:8000/admin).

### Создание и применение миграций

Если вы внесли изменения в модели Django, вам нужно создать и применить новые миграции:

1. Создайте миграции:
   ```bash
   python manage.py makemigrations
   ```

2. Примените миграции:
   ```bash
   python manage.py migrate
   ```

## 4. Запуск фронтенда

Для того чтобы запустить фронтенд, выполните следующие шаги:

1. Перейдите в директорию с фронтендом:
   ```bash
   cd frontend
   ```

2. Установите все зависимости:
   ```bash
   npm install
   ```

3. Запустите фронтенд в режиме разработки:
   ```bash
   npm start
   ```

4. Фронтенд будет доступен по адресу [http://localhost:3000](http://localhost:3000).

## 5. Запуск фронтенда и бэкенда вместе с помощью Docker

Чтобы запустить оба сервиса вместе с помощью Docker, выполните следующие шаги:

1. В корневой директории проекта убедитесь, что у вас установлен Docker.

2. Запустите команду для сборки и запуска контейнеров:
   ```bash
   docker-compose up --build
   ```

3. Бэкенд будет доступен по адресу [http://localhost:8000](http://localhost:8000), а фронтенд — по адресу [http://localhost:3000](http://localhost:3000).

## 6. Остановка контейнеров Docker

Чтобы остановить работу контейнеров, выполните команду:

```bash
docker-compose down
```