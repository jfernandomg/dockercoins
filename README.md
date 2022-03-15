# dockercoins
```
git clone https://github.com/jfernandomg/dockercoins
cd dockercoins
docker network create dockercoins
docker login
docker build -t jfernandomg/ruby:sinatra-thin hasher/
docker push jfernandomg/ruby:sinatra-thin
docker run  --entrypoint ruby --name hasher --read-only --rm -u nobody -v $PWD/hasher/hasher.rb:/data/hasher.rb -w /data/ --network dockercoins jfernandomg/ruby:sinatra-thin hasher.rb
docker pull redis:alpine
docker inspect redis:alpine
docker build -t jfernandomg/redis:alpine redis/ 
docker push jfernandomg/redis:alpine
docker run  --entrypoint docker-entrypoint.sh --name redis --read-only --rm -u redis -w /data/ --network dockercoins jfernandomg/redis:alpine redis-server
docker build -t jfernandomg/python:alpine rng/
docker push jfernandomg/python:alpine
docker run  --entrypoint python --name rng --read-only --rm -u nobody -v $PWD/rng/rng.py:/data/rng.py -w /data/ --network dockercoins jfernandomg/python:alpine rng.py
