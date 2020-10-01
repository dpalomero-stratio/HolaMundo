FROM alpine:latest
USER root
RUN apk --update add openjdk8-jre 
RUN apk update && apk add curl
ARG JAR_FILE
ENTRYPOINT ["java","-jar","hola.jar"]
