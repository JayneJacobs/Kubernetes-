
Container Links

![ContainerLinks](ContainerLinks.png)

```sh
docker run -d --name redis redis:3.2.0
docker ps
docker build -t dockerapp:v0.3
docker build -t dockerapp:v0.3 .
docker build -t dockerapp:v0.3 .
docker run -d -p 5000:5000 --link redis dockerapp:v0.3
docker inspect 6854aa84b737 | grep IP

docker exec -it 6854aa84b737 bash
admin@6854aa84b737:/app$ ping redis
64 bytes from redis (172.17.0.5): icmp_seq=1 ttl=64 time=0.219 ms

docker-compose ps
docker-compose logs
docker-compose logs -f
docker-compose stop
docker-compose rm
```

versioning
use docker-compose build, not docker-compose up
