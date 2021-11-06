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

### 4. Laddar ner senaste versionen av nginx till docker. 

```

docker pull nginx:latest

```

![image](https://user-images.githubusercontent.com/42642927/140614877-6c1e1cf2-a46d-47d3-8659-c30c08699852.png)

### 5. Kollar om jag har några container som körs.

```

docker ps

```

och 

```

docker ps -a

```

![image](https://user-images.githubusercontent.com/42642927/140614956-0fa6914b-f866-47a2-a775-3126b68b7063.png)

### 6. Kör igång en container.

```

docker run -p 8080:80 nginx

```

![image](https://user-images.githubusercontent.com/42642927/140615058-e80f7f70-bad6-4032-988a-0b5cb66675a8.png)


