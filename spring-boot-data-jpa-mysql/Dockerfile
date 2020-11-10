#imagen de 240Mb
FROM adoptopenjdk:15-jdk-openj9 as builder

WORKDIR /usr/src/app

COPY . .

RUN ./mvnw clean package

########
#imagen de 94Mb
FROM adoptopenjdk:15-jre-openj9
ARG HOST
WORKDIR /usr/src/app
COPY --from=builder /usr/src/app/target/*.jar app.jar
EXPOSE 8080
CMD java -jar app.jar
