# Vulnerable Node Express

This is a vulnerable Node Express service meant to be used as a target for security testing tools.

## Build and Run

### Install NPM Dependencies
```shell script
npm install
```

### Initialize SQLite DB
```shell
node bootstrapdb.js
```

### Run
```shell script
DEBUG=myapp:* npm start
```

## Build and Run with Docker

### Build Docker Image
```shell script
docker build --tag stackhawk/nodeexpressvulny .
```

### Run Docker Container
```shell script
docker run --rm --publish 3000:3000 --name nodeexpressvulny stackhawk/nodeexpressvulny
```

### Build and Run in Docker Compose
```shell script
docker-compose up --build --detach
```

## Known Vulnerabilities
* SQL Injection via search box. - `a%'; insert into items values (default, 'hacker item name','bad bad description'); select * from ITEMS where name like  '%banan`
* Cross Site Scripting via search box. - `<script>alert("hey guy");</script>`