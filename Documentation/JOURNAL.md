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