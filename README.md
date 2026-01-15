
Project Overview

This project is a Spring Boot–based REST API designed to demonstrate a layered backend architecture commonly used in Java applications.
It manages a simple Product resource and provides endpoints for creating, retrieving, updating, deleting, and listing products.

The goal of the project is to illustrate:
	•	How REST APIs process HTTP requests
	•	How responsibilities are divided across application layers
	•	How business logic is separated from persistence logic
	•	How data is safely transferred between layers using DTOs

⸻

Application Architecture

The application is organized into the following layers:
	•	Controller (API layer)
	•	DTO layer (Request & Response objects)
	•	Domain layer (Entity)
	•	Service layer (Business logic)
	•	Repository layer (Persistence)
	•	Support layer (Mappers & Exception handling)

Each layer focuses on a specific responsibility and interacts only with neighboring layers.

⸻

API Layer (Controller)

The controller layer serves as the access point for client requests.

Responsibilities:
	•	Handle incoming HTTP requests
	•	Convert JSON data into Java objects
	•	Delegate operations to the service layer
	•	Return appropriate HTTP responses and status codes

Main class: ProductController

Available endpoints:
	•	POST /api/v1/products – Add a new product
	•	GET /api/v1/products/{id} – Retrieve a product by ID
	•	GET /api/v1/products – Retrieve all products
	•	PUT /api/v1/products/{id} – Modify an existing product
	•	DELETE /api/v1/products/{id} – Remove a product

The controller does not contain business logic; it only manages request–response flow.

⸻

Request & Response Layer (DTOs)

DTOs are used to control how data is exchanged between the client and server.

Responsibilities:
	•	Define input and output data structures
	•	Prevent direct exposure of internal domain objects

Main classes:
	•	ProductRequest – Used when creating a product
	•	UpdateProductRequest – Used for updating product data
	•	ProductResponse – Sent back after successful operations
	•	ErrorMessageResponse – Returned when an error occurs

These classes contain only fields and getters/setters, with no logic.

⸻

Domain Layer (Entity)

The domain layer represents the core data model of the application.

Responsibilities:
	•	Define the Product entity
	•	Map objects to database tables using JPA annotations

Main class: Product

The Product entity includes fields such as id and name and uses annotations like @Entity, @Id, and @GeneratedValue to support database mapping.

⸻

Service Layer (Business Logic)

The service layer handles the application’s core logic.

Responsibilities:
	•	Apply validation and business rules
	•	Coordinate between controller, repository, and mapper
	•	Manage product-related operations

Main class: ProductService

Key operations:
	•	create() – Creates and stores a new product
	•	find() – Fetches a product by its ID
	•	update() – Updates existing product data
	•	findAll() – Retrieves all products
	•	delete() – Deletes a product by ID

This layer remains independent of HTTP and database implementation details.

⸻

Repository Layer (Persistence)

The repository layer manages database interactions.

Responsibilities:
	•	Persist entities
	•	Fetch data from the database
	•	Remove records when needed

Main class: ProductRepository

By extending JpaRepository, common CRUD operations are provided automatically without manual implementation.

⸻

Support Layer (Mappers & Exceptions)

The support layer contains utility components that assist the main workflow.

Responsibilities:
	•	Convert between entities and DTOs
	•	Centralize exception handling
	•	Improve maintainability and readability

Main components:
	•	ProductMapper
	•	ProductNotFoundException
	•	ProductExceptionSupplier
	•	GlobalExceptionHandler

⸻

Database and Tools
	•	Database: H2 (in-memory)
	•	ORM Framework: Hibernate with Spring Data JPA
	•	API Documentation: Swagger UI
	•	Testing Tools: Postman and Swagger

The H2 database is used only during runtime and is intended for development and testing purposes.

⸻

Demonstration

The application is tested by sending POST, GET, PUT, and DELETE requests using Postman, and the results are verified directly in the database.

<img width="1440" height="900" alt="post" src="https://github.com/user-attachments/assets/16ac4232-7e50-4ae1-9979-bba33f2ad3e1" />

<img width="1440" height="900" alt="get" src="https://github.com/user-attachments/assets/fcb71d35-b5f8-49e0-9127-3eb46f3490b9" />

<img width="1440" height="900" alt="getC" src="https://github.com/user-attachments/assets/b30a52b0-0ce4-4685-84e7-5f1a8530faaf" />

<img width="1440" height="900" alt="put" src="https://github.com/user-attachments/assets/ede200d4-22c7-457d-b642-b9bab7aed4ee" />

<img width="1440" height="900" alt="putC" src="https://github.com/user-attachments/assets/bfd92794-14f1-4acf-86b9-5722ab72a277" />

<img width="1440" height="900" alt="delete" src="https://github.com/user-attachments/assets/7c2ce8f0-cc10-41b2-a03b-992c69dc1cdb" />

<img width="1440" height="900" alt="deleteC" src="https://github.com/user-attachments/assets/3bf8dffd-99da-4b65-a3a6-85eed8393f8a" />





