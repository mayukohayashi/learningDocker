# Notes

## Assignment1
### Run through simple compose command
- cd sample02(e.g.)
- docker-compose up
- ctrl-c (same as docker-compose stop)
- docker-compose down
- docker-compose up -d
- docker-compose ps
- docker-compose logs
- docker-compose logs web
### While ap is running detached
- docker-compose exec web sh(go to inside of container)
- curl localhost
- exit
### edit Dockerfile, add curl with apk
- Run apk add --update curl
- docker-compose up -d
## Notice it didnt build so force it
- docker-compose up -d --build
### now try curl again
- docker-compose exec web sh curl localhost
<!-- docker-compose exec web sh
/usr/src/app # curl localhost
curl: (7) Failed to connect to localhost port 80: Connection refused
/usr/src/app # curl localhost:3000 -->
- exit

### Clean up
- docker-compose down
-  docker-compose --rmi type (clear images)

### memo
- docker-compose build --no-cache (building not using cache)