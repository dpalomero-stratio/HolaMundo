FROM alpine:latest
USER root
RUN apk --update add openjdk8-jre 
ARG JAR_FILE
ENTRYPOINT ["java","-jar","hola.jar"]
