FROM alpine:latest
USER root
COPY . Hola_Mundo/src/Prueba
WORKDIR Hola_Mundo/src/Prueba
RUN apk --update add openjdk8-jre 
RUN apk update && apk add curl
CMD java -classpath Hola_Mundo/src/Prueba hola
ENTRYPOINT ["java","-jar","hola.jar"]
