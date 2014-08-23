# Spring Boot 1.0 Hello World in Docker

This is a quick tech demo to integrate the buzzwords of the day:
[Spring Boot](http://projects.spring.io/spring-boot/),
[Docker](https://www.docker.io/) and
[Microservices](http://martinfowler.com/articles/microservices.html).

## Compatibility
* This has been tested on various Macs and should work on all Unixes supported
  by Gradle/Docker
* The Dockerfile currently installs a Java7 VM so you can't compile for Java8
* There's no support for Windows since I don't have easy access to machines.
  Therefore, there's no gradlew.bat file to not raise false hopes.

## Requirements
1. Docker

## Features
1. almost self contained (just add docker)
1. up in 5 secs
1. no provisioning framework (puppet, chef, etc.)
1. rebuilt in 10 secs

## HowTo
    # 1. Build the Spring Boot app
    ./gradlew build

    # 2. builds the docker image
    docker build -t 'spring-boot' .

    # 3. run the docker image, exposing the port 8080 to our host
    DOCKER_ID=$(docker run -p 8080:8080 -d spring-boot)

    # 4. Try it!
    curl http://127.0.0.1:8080

    # 5. Kill it!
    docker kill $DOCKER_ID

## NOTE
If you're using
[boot2docker](https://github.com/boot2docker/boot2docker) (e.g. you're
a Mac user and running docker itself in a VM), your
[port redirects](http://docs.docker.io/en/latest/use/port_redirection/)
end up in the VM and will not be visible on your
host. [This](https://gist.github.com/deinspanjer/9215467) script
helps. The original issue is
[here](https://github.com/dotcloud/docker/issues/4007).
