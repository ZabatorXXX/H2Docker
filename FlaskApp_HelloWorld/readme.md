# Del 2, Praktiskt

## 2.1 Flask app

###### 1. Skapa en Dockerfile för appen.

Dockerfile:

```

FROM python:3.9-alpine3.13

COPY . .

RUN pip3 install -r requirements.txt

LABEL maintainer = "Zab"

CMD ["python3", "app.py"]

```

###### 2. När du bygger imagen ska "donotinclude.txt" INTE inkluderas.

donotinclude.txt:

```

textthatshouldnotbeincluded

```

###### 3. Beskriv i Dockerfile vem som är "maintainer" genom att använda en instruktion för meta data.

![Maintainer](https://user-images.githubusercontent.com/42642927/138879685-8b23509b-cb20-4a89-b537-c528163f977a.PNG)

###### 4.Base image ska vara pythons, men det ska vara baserad på python version 3.9 och alpine 3.13.

![Baseimage](https://user-images.githubusercontent.com/42642927/138880228-0dcb641c-8463-4e7a-88b5-6396ae5e2139.PNG)

