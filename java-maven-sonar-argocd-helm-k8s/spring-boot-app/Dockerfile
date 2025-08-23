# Stage 1: Build with Maven and JDK 17
FROM maven:3.9.3-eclipse-temurin-17 AS build
WORKDIR /app

# Copy Maven project files and source code
COPY pom.xml .
COPY src ./src

# Package the application without running tests
RUN mvn clean package -DskipTests

# Stage 2: Run the application with JRE 17 Alpine
FROM eclipse-temurin:17-jre-alpine
WORKDIR /opt/app

# Copy the built JAR from the build stage
COPY --from=build /app/target/spring-boot-web.jar app.jar

# Run the Spring Boot application
ENTRYPOINT ["java", "-jar", "app.jar"]
