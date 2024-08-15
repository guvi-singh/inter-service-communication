

# Microservices Inter-Service Communication

This project demonstrates a basic example of synchronous inter-service communication between microservices. The project consists of three services:

- **Order Service**: Handles order placement requests.
- **Inventory Service**: Manages the inventory of products.
- **Product Service**: Manages product details.

## Overviews

### How It Works

When an order is placed via the **Order Service**, it checks with the **Inventory Service** to verify if there is sufficient quantity available for the requested product. The communication between these services is synchronous, meaning the **Order Service** waits for a response from the **Inventory Service** before proceeding with the order placement.

### Technologies Used

- **Spring Boot**: Microservices are developed using Spring Boot version 3.3.2.
- **REST APIs**: Services communicate via RESTful APIs.
- **Maven**: Build automation tool used for managing dependencies and packaging the application.

### Maven Configuration

The project uses Maven version 3.8.4 or higher. The POM configuration is set as follows:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>3.3.2</version>
        <relativePath/> <!-- lookup parent from repository -->
    </parent>
    <groupId>com.micromart</groupId>
    <artifactId>micromart-parent</artifactId>
    <version>1.0-SNAPSHOT</version>
    <packaging>pom</packaging>
    <modules>
        <module>product-service</module>
        <module>order-service</module>
        <module>inventory-service</module>
    </modules>

    <properties>
        <maven.compiler.source>17</maven.compiler.source>
        <maven.compiler.target>17</maven.compiler.target>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    </properties>
</project>
```

## Project Structure

- **order-service**: Contains the business logic for handling orders. It communicates with the `inventory-service` to validate inventory before confirming an order.
- **inventory-service**: Responsible for managing inventory levels and providing necessary data to the `order-service`.
- **product-service**: Manages product-related data and serves as a foundational service for other microservices.

## Getting Started

### Prerequisites

- Java 17 or higher
- Maven 3.8.4 or higher

### Running the Services

1. Clone the repository:
   ```bash
   git clone https://github.com/guvi-singh/microservices-inter-service-communication.git
   ```
2. Navigate to each service directory and build the project:
   ```bash
   cd order-service
   mvn clean install
   ```
   Repeat the process for `inventory-service` and `product-service`.
3. Run the services:
   ```bash
   mvn spring-boot:run
   ```
   Start with the `product-service`, followed by `inventory-service`, and finally the `order-service`.

### Testing the Application

- Use Postman or any REST client to test the APIs.
- Place an order using the `order-service` API and ensure it communicates with the `inventory-service` to check product availability.

## Contribution

This project was created with help from Sai Upadhyayula. Contributions and suggestions are welcome!
