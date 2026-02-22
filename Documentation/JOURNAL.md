# Project Journal: Government Scheme Eligibility Platform

## Day 1: Project Skeleton & Build Tools
**Date:** 22/02/2026

### What we built
- Initialized a Spring Boot 3.x Maven project using Spring Initializr.
- Configured the embedded web server (Tomcat) via the `spring-boot-starter-web` dependency.
- Set up local Git version control and linked it to a remote GitHub repository via IntelliJ IDEA.

### Why we built it
- To establish the baseline infrastructure. Spring Boot handles the server configuration, and Maven handles dependency management, allowing us to focus strictly on business logic in upcoming phases.

### What went wrong & How we fixed it
- **Issue:** Downloaded the project with the wrong Java version in mind.
- **Fix:** Instead of regenerating the entire project from scratch, manually updated the `<java.version>` property tag to `21` directly inside the `pom.xml` and reloaded the Maven project.

### Key Learning
- **LTS (Long-Term Support):** Production enterprise applications rely on LTS Java versions (like 21 or 25) rather than short-term feature releases (like 24) for stability and long-term security patching.
- **Group ID:** The `com.platform` (or similar) Group ID in Maven dictates the internal Java package directory structure (`src/main/java/com/platform/...`), not the actual web domain.

### Interview Explanation Angle
*"When bootstrapping a new microservice, my first step is to generate the application skeleton using standard build tools like Maven, ensuring the runtime environment targets a stable LTS Java version. I then immediately establish version control before writing any business logic."*

---

## Day 2: Layered Architecture & Entity Modeling
**Date:** 22-02-2026

### What we built
We added 4 core packages (`service`, `entity`, `controller`, and `repository`) inside the main package. We also created a `Scheme` class in the `entity` package, initializing private variables including a primary key ID with auto-increment, which will map directly to columns in our database schema.

### Why we built it
We created these four folders to structure the code according to the separation of concerns:
- **Controller:** Handles incoming HTTP REST requests (GET/POST).
- **Service:** Contains the core business logic.
- **Entity:** Represents the domain model (the database table blueprint).
- **Repository:** Handles database communication and data access.
  By defining the `Scheme` class as an Entity, we allow the ORM to handle database table creation, eliminating the need to write raw SQL via JDBC.

### What went wrong & How we fixed it
We faced an issue where the `@Entity` & `@Id` annotations were not recognized. We realized that during initialization, we only added the `spring-boot-starter-web` dependency (which handles the web server and HTTP requests), but lacked database dependencies. We fixed this by manually adding the `spring-boot-starter-data-jpa` dependency to the `pom.xml`, which resolved the errors.

### Key Learning
We learned that Spring Web handles the web layer, but we explicitly need Spring Data JPA to handle database interactions. The `@Entity` annotation tells the compiler to map the class to a database table, while `@Id` designates the primary key, which we can auto-increment using `@GeneratedValue`.

### Interview Explanation Angle
"To map a Java class to a database table in Spring Boot, I utilize Spring Data JPA. By annotating a standard Java POJO with `@Entity` and defining a primary key with `@Id`, the underlying ORM (Hibernate) automatically maps the object to a relational database table, abstracting away the need for boilerplate JDBC code and manual SQL queries."

---
