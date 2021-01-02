## Installing Redis
 You can access this **[URL](https://redis.io/topics/quickstart)** to install redis 

----
### A. Installing without docker

#### 1. Command to install
```
 wget http://download.redis.io/redis-stable.tar.gz
 tar xvzf redis-stable.tar.gz
 cd redis-stable
 make
```
#### 2. Starting the Redis
```
redis-server
```

#### 3. Check if Redis is working

```
$ redis-cli ping
PONG
```

---

### B. Install using docker

For the details you can access this **[URL](https://hub.docker.com/_/redis)** 

#### 1. Run docker
```
   - if you don't have docker you can install it first
   - https://docs.docker.com/engine/install/
```
#### 2. Install/Start Redis Instance
 - ***Command***
```   
   docker run --name some-redis -d redis
```
- ***Example***
```
  docker run --name single-redis -d redis
```
- ***Another Command***
```
  docker run -d -p 6379:6379 --name single-redis redis
```
#### 3. If you need to start with persistent storage
   - ***Command***
```
docker run --name some-redis -d redis redis-server --appendonly yes
```
- ***Notes*** 
```
  If persistence is enabled, data is stored in the VOLUME /data, which can be used 
  with --volumes-from some-volume-container or -v /docker/host/dir:/data
```
#### 4. Check the redis instance
   -  ***Check Log***       
``` 
docker logs single-redis
```
- ***Connecting via redis-cli in the container***
```
1. docker exec -it single-redis sh
2. redis-cli
3. you can use now
```

- ***Connect from another linked container***
```
1. docker run -it --rm --link single-redis:redis --name redis-cli-1 redis sh
2. redis-cli -h redis
3. Now you can use it
```

 -------


## Clean Up Redis

#### 1. Stop and Remove the container
```
  docker stop single-redis
  docker rm single-redis
```
#### 2. Delete the image
```
  docker image ls
  docker image rm redis
```