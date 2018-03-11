# Docker Nginx SSL failing:

## 1. Setting up SSL:

```bash
export SERVER_NAME='localhost'
mkdir ssl

openssl req -nodes -x509 -newkey rsa:2048 \
  -subj "/CN=$SERVER_NAME" \
  -keyout ssl/default.key \
  -out ssl/default.crt
```

## 2. Building the Dockerfile locally

```bash
docker build . -f Dockerfile -t nginxphpbb
```

## 3. Running the Docker container

```bash
docker run \
-p 443:443 \
--restart always \
--name nginxphpbb \
nginxphpbb
```