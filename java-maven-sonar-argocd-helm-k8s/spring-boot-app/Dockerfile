# Stage 1: build the app
FROM maven:3.8.6-openjdk-17 AS build
WORKDIR /app

COPY pom.xml .
COPY src ./src

RUN mvn clean package -DskipTests

# Stage 2: run the app
FROM adoptopenjdk/openjdk17:alpine-jre
WORKDIR /opt/app

COPY --from=build /app/target/spring-boot-web.jar app.jar

ENTRYPOINT ["java", "-jar", "app.jar"]

