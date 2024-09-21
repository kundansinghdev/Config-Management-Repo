# Stage 1: Build the application using Maven and Amazon Corretto JDK
FROM maven:3.9.8-amazoncorretto-17-al2023 AS build

# Set the working directory inside the container for building the application
WORKDIR /app

# Copy the Maven project descriptor (pom.xml) to the container
# This file contains the dependencies and configuration for Maven
COPY pom.xml .

# Download all dependencies defined in pom.xml without building the app
# Caches dependencies to speed up subsequent builds
RUN mvn dependency:go-offline

# Copy the application source code into the container
# Needed for compilation and packaging
COPY src ./src

# Compile and package the application into a JAR file
# Skips tests to speed up the build process
RUN mvn clean package -DskipTests

# Stage 2: Create a lightweight image to run the application using OpenJDK
FROM openjdk:17-slim-bullseye

# Set the working directory inside the container for running the application
WORKDIR /app

# Copy the JAR file from the build stage into the runtime image
# Transferring the packaged application from the build environment
COPY --from=build /app/target/SendOtpMailApplication-0.0.1-SNAPSHOT.jar app.jar

# Expose port 8080 to allow external access to the application
# Makes the application accessible via port 8080 on the host machine
EXPOSE 8080

# Define the command to run the application when the container starts
# Executes the JAR file with the Java runtime
ENTRYPOINT ["java", "-jar", "app.jar"]











# To run your commands correctly:

#     1. mvn clean: Removes old build files to start fresh.
#     2. docker-compose up: Starts your application’s services as defined in the configuration file.
    
# Ensure you're in the correct directory with your `docker-compose.yml` file before running the second command.