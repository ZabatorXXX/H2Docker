Skapar directorty

```

mkdir DOCKER_P3-P3

```

Gör en Github Action miljö som är våran CI CD del för projekt.

![image](https://user-images.githubusercontent.com/42642927/140624016-9df9487f-7cc7-4cb9-a966-3bd1027ecaff.png)






Skapar upp dockerfile, app.py och :

```

FROM python:3.9-alpine3.13

COPY . .

RUN pip3 install -r requirements.txt

CMD ["python3", "app.py"]

```

app.py

```

from flask import Flask
app = Flask(__name__)

@app.route('/')
def index():
    return '<h1>Hello There</h1>'

if __name__=='__main__':
    app.run(host='0.0.0.0')

```

requirements.txt

```

Flask==2.0.1

```

Bygger Docker imagen.

```

docker image build -t flask-app2_o .

```

Kollar om den skapades.

```

docker image ls 

```

![image](https://user-images.githubusercontent.com/42642927/140625492-38cda230-ac34-4109-8d57-e58effb4f4d5.png)


Skapar lokalt med "-p 5000:5000" + IMAGE ID.

```

docker run -p 5000:5000 -d d78bd05423c4

```

![image](https://user-images.githubusercontent.com/42642927/140625531-d9a72ca4-99d1-411a-93fa-83e901214554.png)

