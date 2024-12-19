#Link Postgres container using Docker

Following tutorial
https://www.youtube.com/watch?v=v1m6pzObDks

### Step 1

Pull and install postgress docker image from docker hub

docker run -d -p 5432:5432 --name db -e POSTGRES_USER=user -e POSTGRES_PASSWORD=password -e POSTGRES_DB=database postgres

received error
The container name "/db" is already in use by container "0ead05d1435256cc2b843d2ef65ac877c01a63878ffa90f52f60de38d17a8b55".

Used the following command to find the container
docker ps -a | grep 0ead
docker ps -a -q | grep 0ead

Used following to delete two exited containers
docker ps -a --filter name=db -f name=odoo -q | xargs docker rm

### Step 2

Pull and install PGadmin

docker run -d -p 5050:80 -e PGADMIN_DEFAULT_EMAIL=user@example.com -e PGADMIN_DEFAULT_PASSWORD=password --name pgadmin --link db:db --name pgadmin dpage/pgadmin4

### Step 3

Create postgres database with a volume

docker run -d -p 5432:5432 --name -v {path}:{mount} db -e POSTGRES_USER=user -e POSTGRES_PASSWORD=password -e POSTGRES_DB=database postgres


