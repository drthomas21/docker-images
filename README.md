#Notes
```
#Create Network Bridge
docker network create --driver bridge --subnet 172.29.0.0/16 --gateway 172.29.0.1 docker-network


#Connect Containers to Bridge
docker network connect --ip 172.29.0.2 docker-network mysql-signz
docker network connect --ip 172.29.0.3 docker-network mysql-wordpress

docker network connect --ip 172.29.0.12 docker-network signz-dev
docker network connect --ip 172.29.0.13 docker-network wordpress-dev

docker network connect --ip 172.29.0.20 docker-network nginx-proxy


#Disconnect Containers from the Bridge
docker network disconnect docker-network mysql-signz
```
