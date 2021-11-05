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

### 1. Skappar ett repository till react som jag vill använda

![image](https://user-images.githubusercontent.com/42642927/140572995-c1112634-1676-4b2a-87b2-c4037726055b.png)

