# ---------- Stage 1: Build ----------
FROM maven:3.9.6-eclipse-temurin-17 as build

WORKDIR /app

# Copy source code
COPY . .

# Build the application
RUN mvn clean package -DskipTests

# ---------- Stage 2: Run ----------
FROM eclipse-temurin:17-jdk-alpine

WORKDIR /app

# Copy JAR from the builder stage
COPY --from=build /app/target/*.jar app.jar

# Run the application
ENTRYPOINT ["java", "-jar", "app.jar"]
