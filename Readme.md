## Dockerfile for installing webMethods Integration Server on RedHat Linux


This Dockerfile installs webMethods Integration Server using Docker on a RedHat Linux server. It uses a CentOS 7 base image, installs Java, and downloads and installs webMethods Integration Server. It also exposes port 5555 for IS administration console.

### Prerequisites
- Docker installed on the RedHat Linux server.


### Instructions
- Clone or download the Dockerfile and response file to a folder on your RedHat Linux server.

- Open a terminal window and navigate to the folder containing the Dockerfile and response file.

- Run the following command to build the Docker image:

```csharp
docker build -t webmethods-is .
```

- After the image is built, run the following command to start the container:

```csharp
docker run -d -p 5555:5555 --name webmethods-is-container webmethods-is
```
This will start the Integration Server in a Docker container and expose port 5555 for IS administration console.

To access the Integration Server administration console, open a web browser and navigate to http://<server-ip-address>:5555.

### Configuration

You can configure the Integration Server by modifying the ISInstallResponseFile.txt file before building the Docker image. This file contains the configuration options for the Integration Server installation, such as the installation directory, the Java version, and the features to install.

### Maintenance

**To stop the container, run the following command:**


```csharp
docker stop webmethods-is-container
```
**To start the container again, run the following command:**



```bash
docker start webmethods-is-container
```

**To remove the container, run the following command:**


```bash
docker rm webmethods-is-container
```

**To remove the Docker image, run the following command:**

```bash
docker rmi webmethods-is
```