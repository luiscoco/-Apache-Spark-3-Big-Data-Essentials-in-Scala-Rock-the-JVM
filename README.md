# Udemy-Apache-Spark-3-Big-Data-Essentials-in-Scala-Rock-the-JVM

## Install Docker Desktop on Windows


## Install IntelliJ Community and install Scala plugin


## Run the PostgreSQL docker-compose file

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

## Run pgAdmin 4 

We are going to run pgAdmin 4 to see the database and tables in the PostgreSQL docker container

We run pgAdmin 4 

![image](https://github.com/luiscoco/Udemy-Apache-Spark-3-Big-Data-Essentials-in-Scala-Rock-the-JVM/assets/32194879/05c5c639-95ef-4a87-9ba7-86069c53c9c4)

Now we register a new Server

![image](https://github.com/luiscoco/Udemy-Apache-Spark-3-Big-Data-Essentials-in-Scala-Rock-the-JVM/assets/32194879/0c254a82-9cc8-4436-8741-d22a74d597b1)

