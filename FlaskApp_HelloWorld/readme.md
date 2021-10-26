# Del 2, Praktiskt

## 2.1 Flask app

###### 1. Skapa en Dockerfile för appen.
```

FROM python:3.9-alpine3.13

COPY . .

RUN pip3 install -r requirements.txt

LABEL maintainer = "Zab"

CMD ["python3", "app.py"]

```
