FROM alpine:latest
USER root
RUN apk --update add openjdk8-jre
RUN apk update && apk add curl
CMD java -classpath Hola_Mundo/src/Prueba hola
ENTRYPOINT ["java","-jar","hola.jar"]
