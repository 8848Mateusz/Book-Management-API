# Book Management API

This project is a simple REST API for managing books. It allows you to create, read, update, and delete books. The project is built using **Java**, **Spring MVC**, and **Jackson** for JSON handling. The application is deployed as a WAR file on a servlet container like Tomcat.

## Features

- **List all books** - View a list of all available books.
- **Add a new book** - Add a new book to the collection.
- **Edit a book** - Update the details of an existing book.
- **Delete a book** - Remove a book from the collection.

## Getting Started

Follow the steps below to set up the project locally.

### Prerequisites

- **Java 11+** installed
- **Maven** installed
- **Git** installed

### Setup

1. **Clone the repository**:

   ```bash
   git clone https://github.com/your-username/Workshop-5.git
    ```

2. **Navigate to the project directory**:
  ```bash
  cd Workshop-5
  ```

3. **Build the project using Maven**:
  ```bash
    mvn clean install
  ```

4. **Run the application**:

- You can run the application by deploying the generated WAR file to a servlet container such as Tomcat.

## Maven Project Configuration (`pom.xml`)

- In the `pom.xml`, you need to set the following properties:

```xml
<properties>
    <maven.compiler.source>11</maven.compiler.source>
    <maven.compiler.target>11</maven.compiler.target>
    <spring-framework.version>5.1.9.RELEASE</spring-framework.version>
</properties>
<packaging>war</packaging>
```

### Dependencies
- The following dependencies are required for the project to work properly:

```xml
<dependencies>
    <!-- Spring MVC for handling web requests -->
    <dependency>
        <groupId>org.springframework</groupId>
        <artifactId>spring-webmvc</artifactId>
        <version>${spring-framework.version}</version>
    </dependency>

    <!-- Servlet API for managing HTTP requests -->
    <dependency>
        <groupId>javax.servlet</groupId>
        <artifactId>javax.servlet-api</artifactId>
        <version>4.0.1</version>
        <scope>provided</scope>
    </dependency>

    <!-- Jackson for automatic conversion of objects to JSON -->
    <dependency>
        <groupId>com.fasterxml.jackson.core</groupId>
        <artifactId>jackson-databind</artifactId>
        <version>2.9.0.pr2</version>
    </dependency>
</dependencies>
```

### Building and Packaging
- This project is packaged as a WAR file. To create a WAR file, Maven will use the following configuration:

```xml
<build>
    <plugins>
        <!-- Maven WAR Plugin to package the project as a WAR -->
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-war-plugin</artifactId>
            <version>3.2.3</version>
            <configuration>
                <failOnMissingWebXml>false</failOnMissingWebXml>
            </configuration>
        </plugin>
    </plugins>
</build>
```

## Running the Application
After building the project, you can deploy the WAR file to a servlet container like Tomcat.

1. Place the generated WAR file in the webapps folder of your Tomcat installation.
2. Start the Tomcat server.
3. The application should now be running on http://localhost:8080/ .
   
## API Endpoints
Here are the available API endpoints:

1. Get all books
GET `/books`

Returns a list of all available books.

### Example response:

```json
{
  "isbn": "9788324631766",
  "title": "Thinking in Java",
  "author": "Bruce Eckel",
  "publisher": "Helion",
  "type": "programming"
}
```
2. Get a book by ID
GET `/books/{id}`

Returns the details of a book by its ID.

3. Add a new book
POST `/books`

Add a new book to the collection. The request body should contain the book details in JSON format.

### Example request:

```json
{
  "isbn": "9788324631766",
  "title": "Thinking in Java",
  "author": "Bruce Eckel",
  "publisher": "Helion",
  "type": "programming"
}
```

4. Update a book
PUT `/books/{id}`

Update the details of an existing book. The request body should contain the updated book details in JSON format.

### Example request:

```json
{
  "isbn": "9788324631766",
  "title": "Thinking in Java - Updated",
  "author": "Bruce Eckel",
  "publisher": "Helion",
  "type": "programming"
}
```

5. Delete a book
DELETE `/books/{id}`

Removes a book from the collection by its ID.

## Testing the API
You can test the API using tools like Postman, curl, or any other HTTP client.

Example curl commands:
- List all books:
  ```bash
  curl -X GET http://localhost:8080/books
  ```
- Add a new book:
  ```bash
  curl -X POST -H "Content-Type: application/json" -d '{"isbn":"12345","title":"New Book","author":"Author Name","publisher":"Publisher","type":"fiction"}' http://localhost:8080/books
   ```
- Update a book:
  ```bash
  curl -X PUT -H "Content-Type: application/json" -d '{"isbn":"12345","title":"Updated Book","author":"Author Name","publisher":"Publisher","type":"fiction"}' http://localhost:8080/books/1
   ```
- Delete a book:
  ```
  bash curl -X DELETE http://localhost:8080/books/1
   ```

## Author
- Mateusz Maciejewski

## License
This project is licensed under the MIT License.
