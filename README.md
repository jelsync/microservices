# Microservicio de cuentas

Microservicio para la gestión de cuentas desarrollado con Spring Boot, parte de una arquitectura de microservicios.

## 🏗️ Arquitectura

Este microservicio forma parte de un sistema distribuido y se encarga de gestionar todas las operaciones relacionadas con cuentas de usuario.

## 🛠️ Tecnologías

- **Java 17+**
- **Spring Boot 3.x**
- **Spring Data JPA**
- **PostgreSQL** (AWS RDS)
- **Maven**

## 📋 Requisitos Previos

- JDK 17 o superior
- Maven 3.6+
- Acceso a base de datos PostgreSQL

## ⚙️ Configuración

### Archivo de Configuración

El archivo `application.yml` contiene la configuración base:

```yaml
spring:
  datasource:
    url: ${DB_URL}
    username: ${DB_USERNAME}
    password: ${DB_PASSWORD}
    driverClassName: org.postgresql.Driver
  jpa:
    hibernate:
      ddl-auto: validate
    show-sql: true
```

> ⚠️ **Nota de Seguridad**: Las credenciales que aparecen en el historial de commits son de ejemplo y **no tienen ningún valor**. Fueron utilizadas únicamente con fines de desarrollo y demostración. Siempre usa variables de entorno para credenciales reales.

## 🗃️ Base de Datos

El microservicio se conecta a una instancia de **PostgreSQL en AWS RDS**. 

### Configuración de RDS

- **Motor**: PostgreSQL
- **Versión**: 74+
- **Puerto**: 5432

### Migraciones

El proyecto utiliza Hibernate con la estrategia `ddl-auto: validate`, lo que significa que no creará ni modificará el esquema automáticamente. Debes gestionar las migraciones manualmente o con herramientas como Flyway o Liquibase.

## 📚 Endpoints Principales

```
GET    /api/fetch?mobileNumber={id}       - Obtener cuenta por ID
POST   /api/create                        - Crear nueva cuenta
PUT    /api/update                        - Actualizar cuenta
DELETE /api/delete?mobileNumber={id}      - Eliminar cuenta
```
Swagger

DireccionIP/swagger-ui/index.html

## 📝 Buenas Prácticas de Seguridad

1. **Nunca commits credenciales reales** en el código
2. Usa **variables de entorno** para información sensible
3. Agrega archivos de configuración local a `.gitignore`:
   ```
   application-local.yml
   application-secrets.yml
   .env
   ```
