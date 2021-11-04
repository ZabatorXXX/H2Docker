# Del 2,3 Praktiskt

## Genomförandet av 2.3

### 1. Grundläggande.

Skapar mig ett "directory" som jag vill använda för uppgiften.

```

mkdir Sql_DockerCompose

```

Förflyttar mig till mappen.

```

cd Sql_DockerCompose
```

Skapar docker-compose.yml filen:

```

version: "3.9" # optional since v1.27.0
services:
  db:
    image: mysql:latest
    ports:
      - "3306:3306"
    volumes:
      - mysql_mydata:/var/lib/mysql
    environment:
      MYSQL_DATABASE: mydb
      MYSQL_USER: iamtheuser
      MYSQL_ROOT_PASSWORD: mypassword
      MYSQL_PASSWORD: mypassword
volumes:
  mysql_mydata:

```

Terminal 1. 

```

docker-compose up

```

Terminal 2.

```

docker container ls

```

![image](https://user-images.githubusercontent.com/42642927/140323757-a88d3716-a1e8-4602-90e1-06166a154318.png)


### 2. Ska du i en annan terminal-flik köra "docker exec -it <container id> sh".

```

docker exec -it 6a19e4914f7f sh

```

![image](https://user-images.githubusercontent.com/42642927/140324948-ff2cb728-1c6a-494b-9e3d-4e24b532d3af.png)

### 3. Väl inne i containern kör du "mysql -u iamtheuser -pmypassword".

![image](https://user-images.githubusercontent.com/42642927/140325788-8211b424-7d27-4adf-8849-20db52056353.png)

### 4. Skapar databasen mydb.

```

USE mydb

```

![image](https://user-images.githubusercontent.com/42642927/140326541-0483df82-2a58-44bd-bcf4-b32924dedd7d.png)

### 5. Skapar tabellen books.

```

CREATE TABLE books(id INT NOT NULL AUTO_INCREMENT, title VARCHAR(50) NOT NULL, PRIMARY KEY(id));

```

![image](https://user-images.githubusercontent.com/42642927/140328706-435569fa-1873-4ae2-b4ac-d45b7f592f2a.png)

### 6. Implementerar värdet.  

```

INSERT INTO books(title) VALUES("jack");

```

![image](https://user-images.githubusercontent.com/42642927/140329107-64ea8b1b-672f-474d-abef-be274ad5c02f.png)

### 7. Kontrollerar om det implementerade värdet finns.

```

SELECT * FROM books;

```

![image](https://user-images.githubusercontent.com/42642927/140330079-af09eb03-7011-4fb6-89ad-2430b93769c2.png)


### (8/9). 8. Gå till terminalen mysql är och trycker CTRL + z. 9. Och terminalen för docker-compose körs och trycker CTRL + c.

![8 9](https://user-images.githubusercontent.com/42642927/140331749-091d0be8-41fe-4c06-80ab-216ce3975e83.png)
