# Udemy-Apache-Spark-3-Big-Data-Essentials-in-Scala-Rock-the-JVM

## 1. Install Docker Desktop on Windows

![image](https://github.com/luiscoco/Udemy-Apache-Spark-3-Big-Data-Essentials-in-Scala-Rock-the-JVM/assets/32194879/98b7d510-89ee-4b59-98ce-225b94fb70d5)

After donwloading the fie double click on it for intalling Docker Desktop in you computer

![image](https://github.com/luiscoco/Udemy-Apache-Spark-3-Big-Data-Essentials-in-Scala-Rock-the-JVM/assets/32194879/bfe185e4-4b2f-4508-979d-dd281db9e985)

**IMPORTANT NOTE**: as a prerrequisite to install Docker Desktop we need to enable Windows **Hyper-V** in our laptop

Hyper-V APIs give users the freedom to build and manage virtual machines or containers at various levels in the virtualization stack.

https://learn.microsoft.com/en-us/virtualization/hyper-v-on-windows/reference/hyper-v-requirements?source=recommendations

![image](https://github.com/luiscoco/Udemy-Apache-Spark-3-Big-Data-Essentials-in-Scala-Rock-the-JVM/assets/32194879/d09fd5da-3fef-4040-a71d-5ebd721276f4)

## 2. Install IntelliJ Community and install Scala plugin

https://www.jetbrains.com/idea/download/?section=windows

![image](https://github.com/luiscoco/Udemy-Apache-Spark-3-Big-Data-Essentials-in-Scala-Rock-the-JVM/assets/32194879/610e6b2d-1d80-4ee4-a4f1-243fb388d197)

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

## 5. Build the Spark images

Run this command. In summary, this Docker command is building an image named "spark-base" with the tag "latest" using the Dockerfile and resources located in the ./docker/base directory.

```
docker build -t spark-base:latest ./docker/base
```

This command is using Docker, a platform for developing, shipping, and running applications in containers. Let me break down the command for you:

**docker build**: This part of the command tells Docker to build an image. An image is a lightweight, standalone, and executable software package that includes everything needed to run a piece of software, including the code, a runtime, libraries, and system tools.

**-t spark-base**:latest: This is an option that allows you to tag the image with a name and optionally a tag. In this case, the image is being tagged as "spark-base" with the tag "latest." The tag is a way to version your images, and "latest" is a commonly used tag to indicate the most recent version.

**./docker/base**: This is the build context. It specifies the location of the Dockerfile and any other files needed for the build. In this case, it points to the base directory under the docker directory.

This is the Dockerfile source code located in "./docker/base" folder.

This Dockerfile essentially creates an environment with **Scala**, **Python**, and **Apache Spark**, configured to work together.

```dockerfile
FROM eclipse-temurin:17-jdk
LABEL author="Daniel Ciocirlan" email="daniel@rockthejvm.com"
LABEL version="0.3"

ENV DAEMON_RUN=true
ENV SPARK_VERSION=3.5.0
ENV HADOOP_VERSION=3
ENV SCALA_VERSION=2.13.12
ENV SCALA_HOME=/usr/share/scala
ENV SPARK_HOME=/spark

RUN apt-get update && apt-get install -y curl vim wget software-properties-common ssh net-tools ca-certificates jq dbus-x11
RUN echo exit 0 > /usr/sbin/policy-rc.d

RUN cd "/tmp" && \
    wget --no-verbose "https://downloads.typesafe.com/scala/${SCALA_VERSION}/scala-${SCALA_VERSION}.tgz" && \
    tar xzf "scala-${SCALA_VERSION}.tgz" && \
    mkdir "${SCALA_HOME}" && \
    rm "/tmp/scala-${SCALA_VERSION}/bin/"*.bat && \
    mv "/tmp/scala-${SCALA_VERSION}/bin" "/tmp/scala-${SCALA_VERSION}/lib" "${SCALA_HOME}" && \
    ln -s "${SCALA_HOME}/bin/"* "/usr/bin/" && \
    rm -rf "/tmp/"*

# Add Dependencies for PySpark
RUN apt-get install -y python3 python3-pip python3-numpy python3-matplotlib python3-scipy python3-pandas python3-simpy
RUN update-alternatives --install "/usr/bin/python" "python" "$(which python3)" 1

#Scala instalation
RUN export PATH="/usr/local/sbt/bin:$PATH" &&  apt update && apt install ca-certificates wget tar && mkdir -p "/usr/local/sbt" && wget -qO - --no-check-certificate "https://github.com/sbt/sbt/releases/download/v1.9.6/sbt-1.9.6.tgz" | tar xz -C /usr/local/sbt --strip-components=1 && sbt sbtVersion -Dsbt.rootdir=true

RUN wget --no-verbose https://archive.apache.org/dist/spark/spark-${SPARK_VERSION}/spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz && tar -xvzf spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz \
      && mv spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION} spark \
      && rm spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz



# Fix the value of PYTHONHASHSEED
# Note: this is needed when you use Python 3.3 or greater
ENV PYTHONHASHSEED 1
```

This Dockerfile seems to be setting up an environment for running Apache Spark with PySpark support along with Scala and Python. Let's break it down step by step:

**Base Image**: It starts with a base image based on the Eclipse Temurin JDK version 17.

```
FROM eclipse-temurin:17-jdk
```

**Labels**: These are metadata labels providing information about the image, such as author and version.

...
LABEL author="Daniel Ciocirlan" email="daniel@rockthejvm.com"
LABEL version="0.3"
...

**Environment Variables**: These set environment variables used throughout the Dockerfile, such as Spark version, Hadoop version, Scala version, Scala home directory, and Spark home directory.

```
ENV DAEMON_RUN=true
ENV SPARK_VERSION=3.5.0
ENV HADOOP_VERSION=3
ENV SCALA_VERSION=2.13.12
ENV SCALA_HOME=/usr/share/scala
ENV SPARK_HOME=/spark
```

**System Packages Installation**: This installs various system packages using apt-get.

```
RUN apt-get update && apt-get install -y curl vim wget software-properties-common ssh net-tools ca-certificates jq dbus-x11
RUN echo exit 0 > /usr/sbin/policy-rc.d
```

**Scala Installation**: It downloads and installs Scala, setting up the necessary environment variables and symbolic links

```
RUN cd "/tmp" && \
    wget --no-verbose "https://downloads.typesafe.com/scala/${SCALA_VERSION}/scala-${SCALA_VERSION}.tgz" && \
    tar xzf "scala-${SCALA_VERSION}.tgz" && \
    # ... (extracting and moving Scala binaries) ...
    rm -rf "/tmp/"*
```

**Python and PySpark Dependencies**: Installs Python 3 and some popular scientific libraries, and updates the Python symbolic link

```
RUN apt-get install -y python3 python3-pip python3-numpy python3-matplotlib python3-scipy python3-pandas python3-simpy
RUN update-alternatives --install "/usr/bin/python" "python" "$(which python3)" 1
```

**Scala Build Tool (SBT) Installation**: Downloads and installs SBT (Scala Build Tool)

```
RUN export PATH="/usr/local/sbt/bin:$PATH" && \
    apt update && apt install ca-certificates wget tar && \
    mkdir -p "/usr/local/sbt" && \
    wget -qO - --no-check-certificate "https://github.com/sbt/sbt/releases/download/v1.9.6/sbt-1.9.6.tgz" | tar xz -C /usr/local/sbt --strip-components=1 && \
    sbt sbtVersion -Dsbt.rootdir=true
```

**Apache Spark Installation**: Downloads and installs Apache Spark.

```
RUN wget --no-verbose https://archive.apache.org/dist/spark/spark-${SPARK_VERSION}/spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz && \
    tar -xvzf spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz && \
    mv spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION} spark && \
    rm spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz
```

**Python Configuration**:

```
ENV PYTHONHASHSEED 1
```

Sets the PYTHONHASHSEED environment variable.



```
docker build -t spark-master:latest ./docker/spark-master
```

```
docker build -t spark-worker:latest ./docker/spark-worker
```

```
docker build -t spark-submit:latest ./docker/spark-submit
```

