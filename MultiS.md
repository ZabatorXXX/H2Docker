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

### 7. Går till http://localhost/ :

Resultat ett innan förändrat index filen: 

```

<h1>Hello World</h1>

```

![image](https://user-images.githubusercontent.com/42642927/140617099-849d19b7-f379-4f19-80b5-3d8bbaa8592b.png)

![image](https://user-images.githubusercontent.com/42642927/140617020-81295592-2072-4e2d-9b7e-850e784e6557.png)


Resultat två efter ändrad index fil och laddat om localhost: 

```

<h1>Hello Woorlds</h1>

```

![image](https://user-images.githubusercontent.com/42642927/140617272-a0e5bb6e-b522-4173-8e0b-961f6ef928e7.png)

![image](https://user-images.githubusercontent.com/42642927/140617233-00db0ae9-f465-468c-9f78-237e55e4921d.png)

