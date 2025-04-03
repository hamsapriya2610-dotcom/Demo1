<img align="left" width="48" height="48" src="./spring-boot-logo.jpg">

# Spring Boot Application Example

[![Build Status](https://travis-ci.org/mertakdut/Spring-Boot-Sample-Project.svg?branch=master)](https://travis-ci.org/mertakdut/Spring-Boot-Sample-Project)
[![Coverage Status](https://coveralls.io/repos/github/mertakdut/Spring-Boot-Sample-Project/badge.svg?branch=master)](https://coveralls.io/github/mertakdut/Spring-Boot-Sample-Project?branch=master)

This is a sample Java / Maven / Spring Boot application that provides RESTful services.  
It can be used as a starter project. Currently, it is designed to work as the [backend](https://github.com/mertakdut/React-Sample-Project) for this project.


## 🚀 Installation

You can import this project as a Maven application into your favorite IDE.  
> ✅ Tested on: **Eclipse JEE 2018-12**

If you encounter issues with Lombok, you can install it manually using the `.jar` file.  
[→ StackOverflow answer](https://stackoverflow.com/a/22332248/4130569)


## ▶️ Running the Application

You can run this Spring Boot application in multiple ways:

### 1. Using Maven
```bash
mvn clean package
java -jar BankApplicationBackend-0.0.1-SNAPSHOT.jar
```

### 2. On Unix/Linux as Executable Jar
```bash
mvn clean package
chmod +x BankApplicationBackend-0.0.1-SNAPSHOT.jar
./BankApplicationBackend-0.0.1-SNAPSHOT.jar
```

### 3. Using Docker
```bash
# Clone the repository
git clone https://github.com/mertakdut/Spring-Boot-Sample-Project.git
cd Spring-Boot-Sample-Project

# Build the Docker image
docker build -t demo/bankapp .

# If you get a './mvnw not found' error, generate the Maven wrapper:
mvn -N io.takari:maven:wrapper -Dmaven=3.5.3

# Run the Docker container
docker run -p 8080:8080 demo/bankapp
```

## 🧪 Testing the Application
  ### 1. Create a User
  ```bash
  curl -X POST localhost:8080/api/user/create \
    -H "Content-Type: application/json" \
    -d '{"username": "yourUsername", "password": "yourPassword", "tcno": "12512561125"}'
  ```
  ```json
  {
    "username": "yourUsername",
    "tcno": "12512561125"
  }
  ```

  ### 2. Generate an Access Token
  ```bash
  curl -X POST http://localhost:8080/api/login \
    -H "Content-Type: application/json" \
    -d '{"username": "yourUsername", "password": "yourPassword"}'
  ```
  
  **Response (sample token):**
  ```text
  eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzUxMiJ9...
  ```
  
  ### 3. Authenticated Requests with Token
  **Get All Users**
  ```bash
  curl -X GET http://localhost:8080/api/user/find/all \
    -H "Accept: application/json" \
    -H "Authorization: Bearer <your-access-token>"
  ```
  **Create a Transaction**
  ```bash
  curl -X POST http://localhost:8080/api/transaction/create \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer <your-access-token>" \
    -d '{
      "username": "yourUsername",
      "buying": true,
      "currency": "USD",
      "amount": "250"
    }'
  ```

  ## ✅ Done!
  You are now ready to explore and extend this Spring Boot sample backend!