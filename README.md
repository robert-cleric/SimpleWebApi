To Run as a Docker container

docker build --rm -t simple-web-api .
docker run --rm -d -p 80:80 simple-web-api