# Docker to the Security

<p align="center">
  <img src="./docker-to-the-security.png?raw=true" alt="Custom Docker image"/>
</p>

This is a collection of Docker related examples for my **Docker to the Security** talk that I gave @ [BSides Leeds 2023](https://bsidesleeds.com/).

You are free to use these examples as you see fit, however please respect any of licences of those 3rd party components that I have used in these examples.

There are several use case for Docker from a security perspective (and not limited to):

* As an eduction tool
* As a means to make it easier to run a security tool
* As a means to running security service easily (using the likes of Docker Compose)
* As a security toolset within a CI/CD pipeline (such as GitHub actions)
* As a research tool

## Basic Example

### simple-http-server

This example is a simple NGinx web server serving static HTML. The static HTML used was downloaded from [https://html5up.net/landed](https://html5up.net/landed).

In order to build and run this exmaple, execture the following:

```shell
docker build -f simple-http-server/Dockerfile -t simple-http-server .
docker run -p 80:80 simple-http-server
```

Alternatively you can download and run this image from [Docker Hub](https://hub.docker.com/r/seanwrightsec/docker-to-the-security):

```shell
docker pull seanwrightsec/docker-to-the-security:simple-http-server
docker run -p 80:80 simple-http-server
```

## As a Eductional Tool

Docker provides a great and safer way of having services with insecure configuration or known vulnerabilities. This is a great way to help from an education point of view, allow security professionals to spin these instances up and show how an attack could potential exploit this insecure configuration or vulnerabilities,

### http-server-trace

This example is a simple Apache HTTPD instance where the configuration has been modified to enable the HTTP TRACE method (setting the configuration option `TraceEnable` to `on`).

In order to build and run this exmaple, execture the following:

```shell
docker build -f http-server-trace/Dockerfile -t http-server-trace .
docker run -p 80:80 http-server-trace
```

Alternatively you can download and run this image from [Docker Hub](https://hub.docker.com/r/seanwrightsec/docker-to-the-security):

```shell
docker pull seanwrightsec/docker-to-the-security:http-server-trace
docker run -p 80:80 http-server-trace
```

## Easier to Run a Standalone Security Tool

Docker can provide a great way to abstract some of the complexities of running security related tooling. Not to mention making it far easier for others to run the tooling (without having the need to go through the process of installing those tools).

### testssl

This example is how you can create a Docker image to make it easy to run security related tooling. In this example, we Docker to help make it simple to run the security tool [testssl.sh](https://testssl.sh/).

In order to build and run this exmaple, execture the following:

```shell
docker build -f testssl/Dockerfile -t testssl .
docker run testssl <site-to-scan>
```

Alternatively you can download and run this image from [Docker Hub](https://hub.docker.com/r/seanwrightsec/docker-to-the-security):

```shell
docker pull seanwrightsec/docker-to-the-security:testssl
docker run testssl <site-to-scan>
```

*Where `<site-to-scan>` is the website which you would like to testssl.sh to scan against (for example `www.google.co.uk`).*

## Running a Security Service

Using Docker along with Docker Compose makes it far easier and simpler to spin up a security related service. This saves a lot of time and frustration, not to mention making it easier for things such as spinning up new instances.

### opencti

This example is a Docker Compose example, allowing one to run an [OpenCTI](https://github.com/OpenCTI-Platform/docker) instance.

In order to build and run this exmaple, execture the following:

```shell
docker-compose up -d
```

You can then access the service on [http://localhost:8080](http://localhost:8080), using the username `admin@opencti.io` and the password `changeme`.

***Please be aware that it takes several minutes for the service to become available.***

## Research Tool

Docker can also be used as a means for researching security vulnerabilities in a piece of software. For example have a look at the [spring-rce-poc](https://github.com/SeanWrightSec/spring-rce-poc) and [CVE-2022-42889-PoC](https://github.com/SeanWrightSec/CVE-2022-42889-PoC) exmaples.