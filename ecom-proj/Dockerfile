# Use an official Maven image with JDK 21 to build the application
FROM maven:3.9.0-openjdk-21 AS build

# Set the working directory in the container
WORKDIR /app

# Copy the pom.xml and src directory to the container
COPY ecom-proj/pom.xml ./ecom-proj/
COPY ecom-proj/src ./ecom-proj/src

# Build the application
RUN mvn -f ecom-proj/pom.xml clean package

# Use an official OpenJDK 21 image to run the application
FROM openjdk:21-jdk

# Set the working directory in the container
WORKDIR /app

# Copy the built JAR file from the build stage
COPY --from=build /app/ecom-proj/target/ecomprojapplication.jar app.jar

# Run the JAR file
ENTRYPOINT ["java", "-jar", "/app/app.jar"]
