# Stage 1: Build stage
FROM maven:3.8.6-openjdk-17-slim AS build
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN mvn clean package -DskipTests

# Stage 2: Run stage
FROM adoptopenjdk:17-jre-alpine
WORKDIR /opt/app
COPY --from=build /app/target/spring-boot-web.jar app.jar
ENTRYPOINT ["java", "-jar", "app.jar"]


