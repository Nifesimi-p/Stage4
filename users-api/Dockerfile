
# Use official OpenJDK as base image
FROM maven:3.8.6-openjdk-11 AS builder

# Set the working directory inside the container
WORKDIR /app


COPY pom.xml .
COPY src src
RUN mvn package -DskipTests

FROM openjdk:11-jre-slim
WORKDIR /app
COPY --from=builder /app/target/*.jar ./users-api.jar
# Expose the application's port (change if needed)
EXPOSE 8083
# Command to run the application
CMD ["java", "-jar", "users-api.jar"]
