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


## Running a cluster with Docker-compose

```
docker-compose up -d

```

Scale the nodes based on number of hosts specified in the docker-compose

```
docker-compose scale node_voltdb=2
```

Finally, you can access the web UI on port **8180** (or whatever you changed it to)


**NOTE:** The community edititon doesn't support adding nodes to scale up your cluster with Docker.
For enterprise edition, feel free to update the docker-compose `node_voltb` command to support this.


Enjoy
