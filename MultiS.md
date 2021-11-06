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

### 4. Skapar upp min dockerfile. 

![image](https://user-images.githubusercontent.com/42642927/140612958-1d10ecb7-c8de-4fd0-990b-3c39b0649018.png)

### 5. Bygger container vi vill använda. 

```

docker build -t nginx_w_server-image:v1 .

```

![image](https://user-images.githubusercontent.com/42642927/140612994-1c42bd52-368c-4e74-8a15-48d0916c95f4.png)
![image](https://user-images.githubusercontent.com/42642927/140613047-9abbf9fb-cbcf-458f-8292-f3ae9a02a99d.png)

### 6. Kör igång containern “nginx_w_server-image:v1” 

```

docker run -d -p 80:80 nginx_w_server-image:v1

```

![image](https://user-images.githubusercontent.com/42642927/140613134-1d5cd02f-1ba6-415a-a93d-f0297a7e9a07.png)

### 7. Kollar om containern finns

```

docker ps

```

![image](https://user-images.githubusercontent.com/42642927/140613228-1947ba40-7508-4b03-b2ca-843eccb9e4ad.png)

### 7. Ser om "Hello World" visas. 

![image](https://user-images.githubusercontent.com/42642927/140613320-b52edee1-1609-44c3-94f1-6327c9f95320.png)

