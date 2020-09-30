FROM alpine:latest
COPY hola.jar ./hola.jar
RUN apk --update add openjdk8-jre
ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-jar","./hola.jar"]
