# MEMORY.md — Memoria Técnica de GestionSEMU Versión 1.1

## Stack Tecnológico y Ecosistema
- **Lenguaje**: Java 17 / Java 21 (LTS)
- **Interfaz Gráfica**: Java Swing (Componentes personalizados, tablas, formularios de despacho)
- **Persistencia y Base de Datos**: JDBC, Patrón DAO (`IncidenteDAO`, `MovilDAO`, `PacienteDAO`, `PersonalDAO`), MySQL (`gestion_semu`).
- **Herramienta de Construcción**: Maven (Compilación, ejecución con `mvn exec:java`) y scripts batch (`compilar.bat`, `ejecutar.bat`).
- **Pruebas**: JUnit 5 (`IncidenteModelTest`).

## Módulos y Arquitectura Principal
- **Gestión de Incidentes (`FrmIncidente` / `IncidenteDAO`)**:
  - Registro y actualización de servicios de emergencia.
  - Manejo robusto de fechas y horas almacenadas en columnas `VARCHAR(20)` de MySQL (actualizadas mediante `ps.setString` para evitar truncamientos o errores de formato con `Timestamp`).
  - Funciones de normalización de formatos de hora (`HH:mm`, `HH:mm:ss`, puntos `.`, un dígito como `9:30`).
- **Gestión de Móviles y Tripulación (`FrmMovil` / `Movil` / `MovilDAO`)**:
  - Asignación de tripulación de emergencia (Médico, Enfermero, Chofer).
  - Control de estados de ambulancias y móviles (`DISPONIBLE`, `EN_INCIDENTE`, etc.).

## Decisiones Clave y Correcciones Realizadas
- **Horarios en VARCHAR(20)**: Se corrigió el DAO de Incidentes para utilizar `ps.setString` en lugar de `ps.setTimestamp` al guardar horas, ya que la base de datos almacena los tiempos como cadenas (`VARCHAR`), garantizando que las actualizaciones persistan correctamente.
- **Control de Versiones**: Repositorio Git en `https://github.com/BasinDev-C/GestionSEMU.git` (rama `main`), con sincronización automática tras cada cambio exitoso.
