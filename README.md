# docker-voltdb


## Running a single instance

```
docker run --name=voltdb --hostname=volt1 -d -p 8180:8080 pkadetiloye/voltdb:6.6 /voltdb-voltdb-6.6/deploy.py 1 0 localhost
```


## Running a cluster

```
docker run --name=v1 --hostname=volt1 -d -p 8080:8080 \
    pkadetiloye/voltdb:6.6 /voltdb-voltdb-6.6/deploy.py 3 1 volt1
docker run --name=v2 --hostname=volt2 --link=volt1:volt1 -d -p 8081:8080 \
    pkadetiloye/voltdb:6.6 /voltdb-voltdb-6.6/deploy.py 3 1 volt1
docker run --name=v3 --hostname=volt3 --link=volt1:volt1 -d -p 8082:8080 \
    pkadetiloye/voltdb:6.6 /voltdb-voltdb-6.6/deploy.py 3 1 volt1
```


## Docker-compose

### Running a single instance
Run a single instance with docker-compose

```
docker-compose up -d
```


### Running a cluster

Todo: find a clean way to run a cluster with docker-compose and be able to scale containers
e.g
```
docker-compose up -d
docker-compse scale voltdb=5

```

## Contributors
Contributors/pull-requests are welcome.
