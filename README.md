# Del 1, Teoretiskt 

## 1.1 Docker och containerteknologi

1. Vad är Docker(plattformen)? 

Docker är en applikation som gör det möjligt för oss att kunna bygga, fördela och administrera upp containrar med hjälp av Docker kod. 

2. Vad är en Docker Image och hur relaterar en sådan till Docker Containers? 

Image där våra specifikationer finns som ser till att vi kan köra våran docker container med vad vi behöver. Helt enkelt en instruktionsbok om vad som behövs. Innehåller programkoden till applikationen, verktygen, de olika länkarna i produkten(dependencies), filer för applikationen att fungera och “libraries”. 

3. Vad innebär containerteknologi? 

Att man kan köra olika program i olika små datorer som är ihopkopplade i ett nätverk. 

4. Vad är Docker Registry? 

Docker Registry är en ”server side” applikation lagrar och distribuerar Docker images. Registret är ”stateless”, mycket skalbar som är open-source, under ”permissive” Apache license. 

5. Hur lyder Docker Linux Kernels arbetsbeskrivning (vad den gör och hur det går till)? 

En Kernelen till delas till olika seperata containrar. Till skillnad från en VM som har var sin kernal. 

![image](https://user-images.githubusercontent.com/42642927/140646682-1feeba0f-ee24-4154-98ae-f508dca7fb27.png)

![image](https://user-images.githubusercontent.com/42642927/140646880-54920d92-70c0-46ab-b5e7-046d55cff5e5.png)


6. På vilket sätt kan Docker och Docker Containers jämföras med fartygstransporter? 

Docker är själva fartyget behöver bensin för att drivas som är datorprocessorn samt docker. Det här hjälper cotainrarna ombord att kunna bli förflyttade(levererade/användbara). 

7. Vad händer när vi har en Dockerfile och kör "docker build ."? Gå igenom build-processen 

Docker build . Innebär att vi vill använda en docker fil som ligger i vårat repo vi är i. Bygg prosesen tar hand om instruktioner vi har get den som exempl att “RUN pip3 install” och “-r requirements.txt”. När filen kör “RUN pip3 install” installeras pip3 till container men “-r requirements.txt” gör så container läser filen requirements.text innerhåll. 

Mängden bygg steg varierar beroende på hur många instruktioner vi till delar den att använda sig av. 

## 1.2 Docker Client

En container föds 

Docker create  

Docker Run 

Docker start 

(Started State) 

Docker stop 

Docker restart 
 
Docker stop 

## 1.3 DOCKER COMPOSE 

| Command  | Description |
| ------------- | ------------- |
| version: "3.8"  | Version av docker compouse  |
| services:  | Var vi lagrar vilka “services” vi vill köra  |
| flask:  | Service 1 |
| container_name: flaskcontainer  | Här namnger vi containern till flaskcontainer   |
| build:  | Bygger/Skapar Docker-compose   |
| context: ./app  | Hittar var “Dockerfile” finns I projektet   |
| dockerfile:  | Vilken fil som bör användas “dev-dockerfile”   |
| ports:  | Ports vi vill använda oss av    |
| - "5000:5000"  | Port ser 5000 från lokala och ser 5000 från container. Port strukturen   |
| depends_on: - db  | Att den behöver bygga “db” först   |
| networks: - flask_app_net  | Visar vilket nätverk som ska användas   |
| db:  | Service 2   |
| container_name: dbcontainer  | Här namnger vi container till dbcontainer   |
| image: postgres:latest  | Tar fram senaste versionen av postgres från Docker hub   |
| restart: always  | En riktlinje   |
| environment:  | Environment variabler vi kan använda   |
| POSTGRES_DB: mydb  | Namnger postges variablen till mydb  |
| POSTGRES_PASSWORD: postgres  | Gör postges variabeln till lösenord   |
| POSTGRES_USER  | Använder postges variabeln som användare   |
| volumes: - postgres_data:/var/lib/postgresql/data/  | För att länka med de lokala filerna till “DB”   |
| networks: - flask_app_net  | Vilket nätverk som vi ska använd   |
| networks:  | Vårt nätverk  |
| flask_app_net:  | Vad vi har namngett nätverket vi använder  |
| driver: bridge  | Vilken driver vi vill använda, “bridge driver”   |
| volumes:  | Gör en lokal volym   |
| postgres_data:  | Vilket namn vi gav den lokala volymen till   |
