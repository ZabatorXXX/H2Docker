Skapar directorty

```

mkdir DOCKER_P3-P3

```

Gör en Github Action miljö som är våran CI CD del för projekt.

![image](https://user-images.githubusercontent.com/42642927/140624016-9df9487f-7cc7-4cb9-a966-3bd1027ecaff.png)






Skapar upp docker-compose.yml:

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
      MYSQL_DATABASE: datamydb
      MYSQL_USER: imightbetheuser
      MYSQL_ROOT_PASSWORD: mypasswordisnotmypassword
      MYSQL_PASSWORD: mypasswordisnotmypassword
volumes:
  mysql_mydata:
  - ./init.sql/:/docker-entrypoint-initdb.d/init.sql
  
```

init.sql:

```

CREATE TABLE table1 (id INT NOT NULL AUTO_INCREMENT, something VARCHAR(50) NOT NULL, PRIMARY KEY(id));
 

INSERT INTO table1(something) VALUES("dave");
INSERT INTO table1(something) VALUES("james");
INSERT INTO table1(something) VALUES("flink");
INSERT INTO table1(something) VALUES("robert"); 

```
