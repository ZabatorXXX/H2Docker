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

RUN npm install

RUN npm build

# production environment
FROM nginx:stable-alpine

COPY ./nginx.conf ./etc/nginx/conf.d/default.conf

COPY --from=Wbuild ./ /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]

```

![image](https://user-images.githubusercontent.com/42642927/140616490-272a53d9-3a9d-4aa3-85b3-93b3996d9dbc.png)

### 5. Bygger upp container utifrån våran dockerfile.

```

docker build -t nginx-docker-multi-stage-build:1.0 .

```

### 6. Kör container som "non-root user".

Imagen jag ska använda:

```

docker images

```

![image](https://user-images.githubusercontent.com/42642927/140616849-447cb223-e138-452e-bf1e-b777738d1b77.png)

```

Docker run -p 80:80 -v ${pwd}:/usr/share/nginx/html 80e195c2528f

```

![image](https://user-images.githubusercontent.com/42642927/140616907-95da706a-350b-4ec5-b4e3-76a729aee9a0.png)

