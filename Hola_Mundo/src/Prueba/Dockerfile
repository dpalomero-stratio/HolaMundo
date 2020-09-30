FROM alpine:latest
ADD hola.class hola.class
RUN apk --update add openjdk8-jre
ENTRYPOINT ["java","-Djava.security.egd=file:/dev/./urandom","-jar","./hola.class"]
