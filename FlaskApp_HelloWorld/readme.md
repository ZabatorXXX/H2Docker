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

![Baseimage](https://user-images.githubusercontent.com/42642927/138880534-1a20bdde-a29d-4b52-8e70-201a6ded674a.PNG)

###### 5.

app.py:

```

from flask import Flask
app = Flask(__name__)

@app.route('/')
def index():
    return '<h1>Hello World</h1>'

if __name__=='__main__':
    app.run(host='0.0.0.0')

```
## Genomförandet av 2.1

Skapar en mapp där jag lägger till koden senare för applikationen.

```

mkdir Flask_HelloWorld

```

Förflyttar mig till mappen.

```

cd Flask_HelloWorld
```

Trycker på  C:\Users\simon\Flask_HelloWorld> med (alt + click) för att öppna mappen i Visual Studio Code. Härefter lägger jag in all kod och specifika filer vi behöver för uppgiften i mappen.

![BandA](https://user-images.githubusercontent.com/42642927/139214886-ea2cc596-82c4-4f20-bd0f-e9f88a9d27ba.PNG)

Bygger Docker imagen.

```

docker image build -t flask-app .

```

Kollar om den skapades.

```

docker image ls 

```
![flaskapp](https://user-images.githubusercontent.com/42642927/139223141-f52b11da-4fa9-4778-935f-fb7aec51fd09.PNG)


Skapar lokalt med "-p 5000:5000" + IMAGE ID.

```

docker run -p 5000:5000 -d 3922c9c19f6b

```

![5000_5000HelloWorld](https://user-images.githubusercontent.com/42642927/139224790-29190786-1ddc-485d-8f85-bbdf901e4dd6.png)

![image](https://user-images.githubusercontent.com/42642927/139227460-afa0bcc4-7ab2-4956-8dd3-3fbe58a197ca.png)


Jag tar container ID bad120272ac3 använder gör den till ett nytt repository. 

```

docker commit bad120272ac3 zabatorxxx/helloworldx-xflaskapp:1.0 

```
