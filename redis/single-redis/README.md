Installing Redis

wget http://download.redis.io/redis-stable.tar.gz
tar xvzf redis-stable.tar.gz
cd redis-stable
make


Starting Redis
redis-server


Check if Redis is working

$ redis-cli ping
PONG




source from : https://redis.io/topics/quickstart




Install using docker

1. Run docker
   - if you don't have docker you can install it first
   - https://docs.docker.com/engine/install/
2. Install/Start Redis Instance
   - docker run --name some-redis -d redis
   - example : docker run --name single-redis -d redis
   - another command : docker run -d -p 6379:6379 --name single-redis redis
3. If you need to start with persistent storage
   - docker run --name some-redis -d redis redis-server --appendonly yes
   - little notes : If persistence is enabled, data is stored in the VOLUME /data, which can be used with --volumes-from some-volume-container or -v /docker/host/dir:/data
4. Check the redis instance
   a. Check Log
     - docker logs single-redis
   b. Connecting via redis-cli in the container
     - docker exec -it single-redis sh
     - redis-cli
     - you can use now
   c. Connect from another linked container
     - docker run -it --rm --link single-redis:redis --name redis-cli-1 redis sh
     - redis-cli -h redis
     - now you can use it
     
For the details you can access here : https://hub.docker.com/_/redis



Clean Up Redis

1. Stop and Remove the container
  - docker stop single-redis
  - docker rm single-redis
2. Delete the image
  - docker image ls
  - docker image rm redis 



