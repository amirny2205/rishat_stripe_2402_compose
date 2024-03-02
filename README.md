docker exec -it 33e4 ./manage.py createsuperuser

docker cp fixture_240229.json 33e4:/root/rishat_stripe/
docker exec -it 33e4 ./manage.py loaddata fixture_240229.json
