# dockercoins
```
git clone https://github.com/jfernandomg/dockercoins
cd dockercoins
docker network create dockercoins
docker login
git pull
docker build -t jfernandomg/ruby:sinatra-thin hasher/
docker push jfernandomg/ruby:sinatra-thin
docker run -d --entrypoint ruby --name hasher --read-only --restart always -u nobody -v $PWD/hasher/hasher.rb:/data/hasher.rb -w /data/ --network dockercoins jfernandomg/ruby:sinatra-thin hasher.rb
docker pull redis:alpine
docker inspect redis:alpine
docker build -t jfernandomg/redis:alpine redis/ 
docker push jfernandomg/redis:alpine
docker run -d --entrypoint docker-entrypoint.sh --name redis --read-only --restart always -u redis -v redis:/data/ -w /data/ --network dockercoins jfernandomg/redis:alpine redis-server
docker build -t jfernandomg/python:flask rng/
docker push jfernandomg/python:flask
docker run -d --entrypoint python --name rng --read-only --restart always -u nobody -v $PWD/rng/rng.py:/data/rng.py -w /data/ --network dockercoins jfernandomg/python:flask rng.py
docker build -t jfernandomg/python:redis-requests worker/
docker push jfernandomg/python:redis-requests
docker run -d --entrypoint python --name worker --read-only --restart always -u nobody -v $PWD/worker/worker.py:/data/worker.py -w /data/ --network dockercoins jfernandomg/python:redis-requests worker.py
docker build -t jfernandomg/node:express-redis webui/
docker push jfernandomg/node:express-redis
docker run -p -d --entrypoint node --name webui --read-only --restart always -u nobody -v $PWD/webui/webui.js:/data/webui.js -w /data/ --network dockercoins jfernandomg/node:express-redis webui.js
```
