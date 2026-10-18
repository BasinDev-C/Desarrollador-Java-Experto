# MEMORY.md — Memoria Técnica del Proyecto Backend en Java

## Stack Tecnológico y Ecosistema
- **Lenguaje**: Java 17 / Java 21 (LTS)
- **Framework**: Spring Boot 3.x
- **Persistencia**: Spring Data JPA, Hibernate, Flyway / Liquibase (Migraciones de Base de Datos)
- **Bases de Datos**: PostgreSQL (Relacional principal), Redis (Caché y gestión de sesiones)
- **Herramienta de Construcción**: Maven / Gradle (Kotlin DSL)
- **Pruebas**: JUnit 5, Mockito, Testcontainers, RestAssured
- **Contenedores y CI/CD**: Docker, Docker Compose, GitHub Actions

## Pautas Arquitectónicas
- **Arquitectura en Capas**: Controlador -> Servicio -> Repositorio -> Base de Datos.
- **Patrón DTO**: Nunca expongas entidades de base de datos directamente a la capa de API; utiliza siempre DTOs de Solicitud/Respuesta y MapStruct para el mapeo.
- **Manejo de Excepciones**: Manejador global de excepciones (`@RestControllerAdvice`) que retorne detalles de problemas estandarizados (RFC 7807).
- **Buenas Prácticas en Base de Datos**: Evita el problema de consultas N+1 (utiliza `@EntityGraph`, `JOIN FETCH` o carga por lotes), y asegura índices adecuados en claves foráneas y columnas de búsqueda frecuente.

## Estado Actual del Proyecto
- [ ] Inicialización de la arquitectura backend empresarial.
- [ ] Configuración de pools de conexiones a base de datos y scripts de migración.
- [ ] Implementación de modelos de dominio y capas de seguridad.

## Decisiones Clave
- **Java 17/21 LTS**: Seleccionado por su soporte a largo plazo, mejoras de rendimiento y construcciones modernas del lenguaje (Records).
- **Flyway**: Elegido para el control de versiones y migraciones automatizadas del esquema de base de datos.
