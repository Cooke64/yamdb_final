# yamdb_final
![example workflow](https://github.com/Cooke64/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)
# Проект YaMDb

## Описание

Данный проект представляет собой онлайн магазин,в котором реализованы следующие **возможности**:

- Проект YaMDb собирает отзывы пользователей на произведения.
- Произведения делятся на категории: «Книги», «Фильмы», «Музыка». Список категорий  может быть расширен администратором.
- Сами произведения в YaMDb не хранятся, здесь нельзя посмотреть фильм или послушать музыку.
- В каждой категории есть произведения: книги, фильмы или музыка. Например, в категории «Книги» могут быть произведения «Винни-Пух и все-все-все» и «Марсианские хроники», а в категории «Музыка» — песня «Давеча» группы «Насекомые» и вторая сюита Баха.
- Произведению может быть присвоен жанр  из списка предустановленных. Новые жанры может создавать только администратор.
- Благодарные или возмущённые пользователи оставляют к произведениям текстовые отзывы  и ставят произведению оценку в диапазоне от одного до десяти; из пользовательских оценок формируется усреднённая оценка произведения — рейтинг. На одно произведение пользователь может оставить только один отзыв.

## Технлологии

- Django
- Django DRF
- PostgreSql
- Docker

## Клонировать репозиторий и перейти в него в командной строке:

```git clone git@github.com:Cooke64/api_yamdb.git```
Создать файл .env, в котором необходимо создать переменные:
- SOCIAL_AUTH_VK_OAUTH2_KEY
- SOCIAL_AUTH_VK_OAUTH2_SECRET
- EMAIL_HOST_USER
- EMAIL_HOST_PASSWORD
- SECRET_KEY
- DB_NAME
- POSTGRES_USER
- POSTGRES_PASSWORD
- DB_PORT 
## Как запустить проект
- cd infra
- Собрать и запустить все сервисы командой: docker-compose up -d
##Выполнить команды по очереди.
- docker-compose exec web python manage.py migrate
- docker-compose exec web python manage.py createsuperuser
- docker-compose exec web python manage.py collectstatic --no-input
##При завершении работы выполнить команду для удаления контейнеров 
- docker-compose down

**1.post Добавление новой категории  localhost/api/v1/categories/:**
- :white_check_mark:Права доступа: Администратор.
```
{
    "name": "string",
    "slug": "string"
}
```
- :white_check_mark:  Пример успешного ответа:
```
{
    "name": "string",
    "slug": "string"
}
```
**2.get Получение списка всех жанров  localhost/api/v1/genre/:**
- :white_check_mark: Права доступа: Доступно без токена. Пример успешного ответа:
```
[
    {
        "count": 0,
        "next": "string",
        "previous": "string",
        "results": []
    }
]
```
**3. post Регистрация нового пользователя эндоинт localhost/api/v1/auth/signup/:**
- :white_check_mark:  Права доступа: Доступно без токена.
```
{
    "email": "string",
    "username": "string"
}
```
- :white_check_mark:  Пример успешного ответа:
```
{
    "email": "string",
    "username": "string"
}
```
## Документация представлена [здесь](http://localhost/redoc/)
