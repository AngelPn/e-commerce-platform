# Create a new build stage from the base image Gradle that includes JDK 17 to build the backend
FROM gradle:7.3.3-jdk17 AS build
WORKDIR /app
COPY build.gradle /app/
COPY src /app/src
RUN gradle build -x test

# Use OpenJDK 17 for running the application
FROM openjdk:17-slim
COPY --from=build /app/build/libs/*.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "/app.jar"]
