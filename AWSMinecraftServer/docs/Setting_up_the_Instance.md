# Setting up the Instance

This topic covers the steps to setup and run a Minecraft Java Server on the Instance.

## Installing Java

Ensure the Instance has the proper tools to install Java.

```bash
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install software-properties-common ca-certificates apt-transport-https gnupg curl
```

Import the Amazon Corretto public key and apt repository.

```bash
curl https://apt.corretto.aws/corretto.key | sudo apt-key add -
sudo add-apt-repository 'deb https://apt.corretto.aws stable main'
```

Install Java and other dependencies using the following commands.

```bash
sudo apt-get update
sudo apt-get install -y java-21-amazon-corretto-jdk libxi6 libxtst6 libxrender1
```

Verify installation by running the following command.

```bash
java -version
```

The output should look similar to this.

```bash
openjdk version "21" 2023-09-19 LTS
OpenJDK Runtime Environment Corretto-21.0.0.35.1 (build 21+35-LTS)
OpenJDK 64-Bit Server VM Corretto-21.0.0.35.1 (build 21+35-LTS, mixed mode, sharing)
```

## Downloading the Paper Server JAR

Download the Paper Server JAR from the [PaperMC website](https://papermc.io/downloads).

Example download for Paper 1.20.2 Build 309.

```bash
curl https://api.papermc.io/v2/projects/paper/versions/1.20.2/builds/309/downloads/paper-1.20.2-309.jar > paper.jar
```

## Running the Server

Run the server using the following command.

```bash
java -Xms2G -Xmx2G -jar paper.jar --nogui
```

The server will generate the files needed to run the server.

The amount of RAM allocated to the server can be changed by changing the values after `-Xms` and `-Xmx`.

`--nogui` is used to run the server without a GUI.

## Good Documentations

- [PaperMC](https://docs.papermc.io/paper)
