# Udemy-Apache-Spark-3-Big-Data-Essentials-in-Scala-Rock-the-JVM

## 1. Install Docker Desktop on Windows


## 2. Install IntelliJ Community and install Scala plugin


## 3. Run the PostgreSQL docker-compose file

This is the docker-compose.yml file source code:

```yaml
version: '2'

services:
  postgres:
    image: postgres:latest
    container_name: postgres
    environment:
      - "TZ=Europe/Amsterdam"
      - "POSTGRES_USER=docker"
      - "POSTGRES_PASSWORD=docker"
    ports:
      - "5432:5432"
    volumes:
      - "./sql:/docker-entrypoint-initdb.d"
```

We run the PosgreSQL docker container with the following command:

```
docker-compose up
```

![image](https://github.com/luiscoco/Udemy-Apache-Spark-3-Big-Data-Essentials-in-Scala-Rock-the-JVM/assets/32194879/cca697f7-71ff-465b-b7a2-d6285912d9b5)

![image](https://github.com/luiscoco/Udemy-Apache-Spark-3-Big-Data-Essentials-in-Scala-Rock-the-JVM/assets/32194879/52b5759d-fffe-4241-9dec-f1b5d02591c8)

We see in Docker Desktop the PostgreSQL container running, the corresponding docker image and attached volume

![image](https://github.com/luiscoco/Udemy-Apache-Spark-3-Big-Data-Essentials-in-Scala-Rock-the-JVM/assets/32194879/f548888e-b519-43d0-89f0-ae7d6d721c97)

![image](https://github.com/luiscoco/Udemy-Apache-Spark-3-Big-Data-Essentials-in-Scala-Rock-the-JVM/assets/32194879/6598de5e-8ba8-47f9-b452-0461f5e0910d)

![image](https://github.com/luiscoco/Udemy-Apache-Spark-3-Big-Data-Essentials-in-Scala-Rock-the-JVM/assets/32194879/728d92a7-b253-49c9-9a08-2d22d7a89786)

We enter in the PosgreSQL container we run the following command:

```
docker exec -it postgres psql -U docker -d rtjvm
```

This is a command that uses Docker to interact with a PostgreSQL container. Let's break it down:

**docker exec**: This command allows you to run a command inside a running container.

**-it**: These are options for interactive mode. -i stands for interactive, and -t allocates a pseudo-TTY. Together, they allow you to interact with the command you are running inside the container.

**postgres**: This is the name or ID of the Docker container where you want to execute the command. In this case, it's assumed that there's a PostgreSQL container running with the name "postgres."

**psql**: This is the PostgreSQL command-line tool. It's used for interacting with PostgreSQL databases.

**-U docker**: This specifies the username to connect to the PostgreSQL database. In this case, it's set to "docker."

**-d rtjvm**: This specifies the name of the PostgreSQL database to connect to. In this case, it's "rtjvm."

So, in summary, this command is entering an interactive mode inside a running PostgreSQL Docker container named "postgres" and running the psql command to connect to the "rtjvm" database with the username "docker." This is useful for directly interacting with the PostgreSQL database inside the container.

To list the available database we run the command:

```
\l
```

 To list the tables in the "rtjvm" database we run the command:

```
\dt
```

We can see the rows in the "departments" table:

```
select * from departments;
```

![image](https://github.com/luiscoco/Udemy-Apache-Spark-3-Big-Data-Essentials-in-Scala-Rock-the-JVM/assets/32194879/07554b78-654d-4b6f-bd6b-634796cead66)

## 4. Run pgAdmin 4 

We are going to run pgAdmin 4 to see the database and tables in the PostgreSQL docker container

We run pgAdmin 4 

![image](https://github.com/luiscoco/Udemy-Apache-Spark-3-Big-Data-Essentials-in-Scala-Rock-the-JVM/assets/32194879/05c5c639-95ef-4a87-9ba7-86069c53c9c4)

Now we register a new Server

![image](https://github.com/luiscoco/Udemy-Apache-Spark-3-Big-Data-Essentials-in-Scala-Rock-the-JVM/assets/32194879/0c254a82-9cc8-4436-8741-d22a74d597b1)

We input the new Server data

![image](https://github.com/luiscoco/Udemy-Apache-Spark-3-Big-Data-Essentials-in-Scala-Rock-the-JVM/assets/32194879/b89014ba-9702-4971-8ae5-5aecaca60844)

![image](https://github.com/luiscoco/Udemy-Apache-Spark-3-Big-Data-Essentials-in-Scala-Rock-the-JVM/assets/32194879/ed9a05ec-aeda-41fc-9970-2eeb2d770cfb)

We can see a new Server was added in the tree

![image](https://github.com/luiscoco/Udemy-Apache-Spark-3-Big-Data-Essentials-in-Scala-Rock-the-JVM/assets/32194879/60ace434-e9c0-43e3-971d-ea856d4aeef6)

If we expand the new server tree we can see the new database "rtjvm" and tables inside

![image](https://github.com/luiscoco/Udemy-Apache-Spark-3-Big-Data-Essentials-in-Scala-Rock-the-JVM/assets/32194879/7baf7839-d4ac-447e-afe7-958b658f525f)

## 5. 

