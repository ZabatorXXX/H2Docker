### 1. Grundläggande.

Skapar directorty

```

mkdir DOCKER_P3-P3

```
Förflyttar mig till mappen.

```

cd DOCKER_P3-P3

```


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
### 2. Flask app 2.0 med CI CD

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

![5000Hellothere](https://user-images.githubusercontent.com/42642927/140625615-dbe0d570-5ec7-4ddf-8d1b-5b6732bb3ed2.png)

```

docker ps -a

```

![image](https://user-images.githubusercontent.com/42642927/140625683-61f1e5b4-d380-4f69-bd86-58804f5e4de5.png)

### 3. Lokala repot jag ska använda mig av. 

Jag tar container ID b56747f13c27 använder gör den till ett nytt repository.

```

docker commit b56747f13c27 zabatorxxx/hellotherex-xflask_cicd_app:1.0

```

![image](https://user-images.githubusercontent.com/42642927/140625767-f96d6e4f-3cc8-4414-85ae-8eca0884eb93.png)

Söker om repot jag behöver finns.

![image](https://user-images.githubusercontent.com/42642927/140625796-ac21254e-1d08-4f9a-a5c3-dca343f9ef87.png)

### 4. CI CD med Github Action

Gör en Github Action miljö som är våran CI CD del för projekt.

![image](https://user-images.githubusercontent.com/42642927/140624016-9df9487f-7cc7-4cb9-a966-3bd1027ecaff.png)

.github/workflows/main.yml

main.yml:

```

name: Docker CI & CD

# Controls when the workflow will run
on:
  # Triggers the workflow on push or pull request events but only for the main branch
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]
    
# A workflow run is made up of one or more jobs that can run sequentially or in parallel    
jobs:

  # This workflow contains a single job called "build"
  build:
  
    # The type of runner that the job will run on
    runs-on: ubuntu-latest
    
    # Steps represent a sequence of tasks that will be executed as part of the job
    steps:
    
       # Checks-out your repository under $GITHUB_WORKSPACE, so your job can access it
     - uses: actions/checkout@v2

      
     - name: Docker build
       run: |

```

