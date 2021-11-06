# Del 2, Praktiskt

## 2.2 Multi-stage Build

index.html

```

<h1>Hello World</h1>

```

nginx.conf

```

server {
  listen 80;
  
  location / {
    root /usr/share/nginx/html;
    index index.html;
  }
}

```

### 1. Skapar ett repository "nginx-docker-multi-stage-build" för react som jag vill använda mig av. 

```

mkdir nginx-docker-multi-stage-build

```

### 2. Förflyttar mig till repot.

```

cd nginx-docker-multi-stage-build

```

### 3. Skapar upp filerna index.html och nnginx.conf i mappen. 

![image](https://user-images.githubusercontent.com/42642927/140612529-9672093a-0ca0-4941-a89e-22c13cd0c906.png)

### 4. Bygger Dockerfile med:

```

# build environment
FROM node:14-alpine as Wbuild

WORKDIR /app

COPY . .

RUN yarn

RUN yarn build

# production environment
FROM nginx:stable-alpine
COPY --from=Wbuild /app/build /usr/share/nginx/html
COPY --from=Wbuild /app/nginx/nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]

```
