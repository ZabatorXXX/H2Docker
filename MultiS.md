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

npx create-react-app nginx-docker-multi-stage-build

```

![image](https://user-images.githubusercontent.com/42642927/140572995-c1112634-1676-4b2a-87b2-c4037726055b.png)

### 2. Förflyttar mig till repot.
```

cd nginx-docker-multi-stage-build

```

![image](https://user-images.githubusercontent.com/42642927/140573694-779034f6-e97c-43a6-bb4a-a36734dfa59c.png)

### 3. Skriver in “npm start” för live-reload och andra funktiner.

Vilket resulterade till :

![image](https://user-images.githubusercontent.com/42642927/140574678-77897d77-7c94-4c3f-9229-76765df7a504.png)
![image](https://user-images.githubusercontent.com/42642927/140574642-fcea44f6-d442-48bd-bcda-e4e1c81c611e.png)

