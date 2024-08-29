# senthilnathan.js.org
The Cert-Renewal Component is hosted in aPaaS and is developed using Java 17 with Spring Boot 3.0. The application is containerized using Docker, which is used to build and push executables as images.

For CI/CD, Jenkins is employed to manage the stages, including pushing the Docker images to Nexus and deploying the application to the aPaaS environment.

This service integrates with Venafi TPP using mTLS for secure communication, with OAuth being utilized for authentication and authorization operations.
