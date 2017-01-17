# booktype_with_docker
A [booktype](https://www.sourcefabric.org/en/booktype/) in a docker container. It is using sqlite as backend.

# quick start #

Clone my repo
```
git clone https://github.com/ae-m/booktype_with_docker.git
```
Run the ansible roll-out script. It creates the docker container on your local machine.
```
cd ./booktype_with_docker/ansible
su -c 'ansible-playbook booktype_with_docker'
```
Check that all container are running now:
```
[root@host/~]# docker ps
CONTAINER ID        IMAGE                  COMMAND                  CREATED             STATUS              PORTS                               NAMES
89ddb07ce27d        aveelken/booktype	   "/bin/bash start.sh"     About an hour ago   Up About an hour    8000/tcp, 0.0.0.0:49108->8080/tcp   booktype
301e57e02bf4        redis                  "/entrypoint.sh redis"   2 hours ago         Up 2 hours          6379/tcp                            booktyperedis
f60f86fb056c        postgres               "/docker-entrypoint.s"   2 hours ago         Up 2 hours          5432/tcp                            booktypepostgres
```
For trouble-shouting log into the container and start the service manual:
```
[root@host/~]# docker exec -it booktype /bin/bash
root@89ddb07ce27d:/# /bin/bash start.sh

```

# Build images #

```
bash -c 'cd && docker build -t localhost/booktype .'
bash -c 'docker tag localhost/booktype localhost/booktype'
```

You can find a preconfigured image on [hub.docker.com]([https://hub.docker.com/r/aveelken/booktype/)

# Run container (with ansible) #

```
bash -c 'cd ./ansible && ansible-playbook ./run_booktype.yml '
```

# Other docus #

* [install booktype docs](http://sourcefabric.booktype.pro/booktype-20-for-authors-and-publishers/installation-on-gnulinux/)
* [RabbitMQ as docker container](https://hub.docker.com/_/rabbitmq/)
* [PostgreSQL as docker contaner](https://hub.docker.com/_/postgres/)
