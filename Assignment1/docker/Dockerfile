# ✅ Use Java 17 base image *with* apt-get support
FROM openjdk:17-slim

# ✅ Install 'find' by adding findutils
RUN apt-get update && apt-get install -y findutils

# Create app directory inside container
WORKDIR /app

# Copy all source code into the container
COPY src /app/src

# ✅ Make sure output directory exists
RUN mkdir -p /app/bin

# ✅ Use find to locate and compile all Java files
RUN javac -d /app/bin $(find /app/src -name "*.java")

# Set working dir to compiled classes
WORKDIR /app/bin

# Set default class to run if none is provided (LandManagement system)
ENV MAIN_CLASS=LandManagementSystem.Qn2.LandRegistryMain

# 🧼 Use JSON array form for CMD to avoid signal issues
CMD ["sh", "-c", "java ${MAIN_CLASS:-LandManagementSystem.Qn2.LandRegistryMain}"]
