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

!(https://1drv.ms/u/s!As9tV0LY9I3_gf1lCyVbpMRxLHY84g)

