# Create a new build stage from the base image Gradle that includes JDK 17 to build the backend
FROM gradle:7.5-jdk17 AS build
WORKDIR /app
COPY . .
RUN gradle build -x test

FROM openjdk:17-jdk-slim
WORKDIR /app
COPY --from=build /app/build/libs/*.jar app.jar
ENTRYPOINT ["java", "-jar", "app.jar"]