# -------- Build stage --------
FROM maven:3.9.6-eclipse-temurin-17 AS builder
WORKDIR /app

# Clone your backend repo (update this with your repo URL)
RUN git clone https://github.com/Keerthana-Javvaji/docker-ecommerce-backend.git .

# Build the Spring Boot JAR
RUN mvn clean package -DskipTests

# -------- Run stage --------
FROM eclipse-temurin:17-jdk-alpine
WORKDIR /app

# Copy JAR file from builder
COPY --from=builder /app/target/*.jar app.jar

EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]
