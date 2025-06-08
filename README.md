# REST Service - Spring Boot POC

This project is a proof of concept (POC) based on the official Spring Boot example "gs-rest-service". It has been adapted to support dual deployment:

- **WAR**: for application servers like WildFly.
- **JAR**: for standalone execution or in containers (Docker, Kubernetes, Fargate, etc).

## Project structure

- `src/main/java` - Application source code.
- `src/test/java` - Unit tests integrated into the CI/CD cycle.
- `pom.xml` - Maven configuration with WAR and JAR profiles.
- `mvnw`, `mvnw.cmd`, `.mvn/` - Maven Wrapper for portable and consistent builds.
- `.github/workflows/ci-cd.yml` - GitHub Actions workflow for CI/CD.

## Maven profiles

- **jar** (default):
  - Generates an executable JAR with embedded Spring Boot.
  - Command: `./mvnw clean package -Pjar`
- **war**:
  - Generates a WAR for deployment on servers like WildFly.
  - Command: `./mvnw clean package -Pwar`

## Local execution

### As JAR (standalone)

```bash
./mvnw clean package -Pjar
java -jar target/rest-service-complete-0.0.1-SNAPSHOT.jar
```

#### As WAR (WildFly, Tomcat, etc)

```bash
./mvnw clean package -Pwar
# Copy the WAR generated in target/ to your server's deployment directory
```

### Tests

To run the tests:

```bash
./mvnw test
```

## CI/CD (GitHub Actions)

The main workflow is in `.github/workflows/ci-cd.yml` and performs:

- **Build**: Compiles and packages the project as JAR or WAR according to the `build_type` input (default JAR).
- **Test**: Runs unit tests.
- **Publish**: Extracts and displays the version from pom.xml using the `s4u/maven-version-action` action.
- **Deploy**: Simulates a deployment by displaying the version extracted from pom.xml.

You can trigger the workflow manually from GitHub Actions by selecting the artifact type (JAR or WAR), or it will run automatically on every push/pull request to the `main` branch.

## Credits

Based on the official Spring Boot example: <https://github.com/spring-guides/gs-rest-service>

---

Este proyecto es una prueba de concepto (POC) basada en el ejemplo oficial de Spring Boot "gs-rest-service". Se ha adaptado para soportar despliegue dual:

- **WAR**: para servidores de aplicaciones como WildFly.
- **JAR**: para ejecución standalone o en contenedores (Docker, Kubernetes, Fargate, etc).

## Estructura del proyecto

- `src/main/java` - Código fuente de la aplicación.
- `src/test/java` - Pruebas unitarias integradas en el ciclo CI/CD.
- `pom.xml` - Configuración Maven con perfiles para WAR y JAR.
- `mvnw`, `mvnw.cmd`, `.mvn/` - Maven Wrapper para builds portables y consistentes.
- `.github/workflows/ci-cd.yml` - Workflow de GitHub Actions para CI/CD.

## Perfiles Maven

- **jar** (por defecto):
  - Genera un JAR ejecutable con Spring Boot embebido.
  - Comando: `./mvnw clean package -Pjar`
- **war**:
  - Genera un WAR para desplegar en servidores como WildFly.
  - Comando: `./mvnw clean package -Pwar`

## Ejecución local

### Como JAR (standalone)

```bash
./mvnw clean package -Pjar
java -jar target/rest-service-complete-0.0.1-SNAPSHOT.jar
```

### Como WAR (WildFly, Tomcat, etc)

```bash
./mvnw clean package -Pwar
# Copia el WAR generado en target/ al directorio de despliegue de tu servidor
```

## Pruebas

Para ejecutar los tests:

```bash
./mvnw test
```

## CI/CD (GitHub Actions) [ES]

El workflow principal está en `.github/workflows/ci-cd.yml` y realiza:

- **Build**: Compila y empaqueta el proyecto como JAR o WAR según el input `build_type` (por defecto JAR).
- **Test**: Ejecuta los tests unitarios.
- **Publish**: Extrae y muestra la versión del pom.xml usando la acción `s4u/maven-version-action`.
- **Deploy**: Simula un despliegue mostrando la versión extraída del pom.xml.

Puedes lanzar el workflow manualmente desde GitHub Actions seleccionando el tipo de artefacto (JAR o WAR), o se ejecutará automáticamente en cada push/pull request a la rama `main`.

## Créditos

Basado en el ejemplo oficial de Spring Boot: <https://github.com/spring-guides/gs-rest-service>

---

Questions or suggestions? Contribute or open an issue!

¿Dudas o sugerencias? ¡Contribuye o abre un issue!
