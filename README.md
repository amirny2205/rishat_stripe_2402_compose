### Описание сервиса
Сервис представляет собой выполнение вот этого [тестого задания](https://docs.google.com/document/d/1fEjqKUwsPOXPLeeFJL8GqKzfC755Ancnu1y1zQbBA4o/edit?usp=sharing)

### Инструкция по запуску
Скопировать репозитории https://github.com/amirny2205/rishat_stripe_2402_nginx и https://github.com/amirny2205/rishat_stripe_2402_django в ту же папку, где находится текущая.

Структура папки будет выглядеть как:  
```
.
..
rishat_stripe_2402_django
rishat_stripe_2402_compose
rishat_stripe_2402_nginx
```

Исполнить: `cp ./.env_docker_compose_example ./.env_docker_compose`  
Заполнить его соответственно  
`CHECKOUT_RETURN_URL` - это абсолютный путь к странице с _payment_submit/_, его использует скрипт stripe на странице _checkout/_ . Заменить, когда ваш итоговый хостнейм будет отличаться.  
`ALLOWED_HOSTS` автоматически добавляются к уже имеющемуся списку (`['localhost', '127.0.0.1']`)

Запустить сервис: 
`docker compose up` или `docker-compose up`

Теперь на `localhost/items/` браузер должен показывать страницу с выбором вещей.


### Дополнительные команды
Подгрузить фикстуру(можно взять готовую, указанную в https://github.com/amirny2205/rishat_stripe_2402_django )  
```
docker cp fixture_240229.json 33e4:/root/rishat_stripe/
docker exec -it 33e4 ./manage.py loaddata fixture_240229.json
```

Создать админа  
```docker exec -it 33e4 ./manage.py createsuperuser```


