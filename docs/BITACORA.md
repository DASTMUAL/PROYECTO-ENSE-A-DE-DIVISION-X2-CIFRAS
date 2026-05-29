# Bitácora de Desarrollo - Proyecto Plataforma Educativa

## Semana 1: Inicialización del Ecosistema
* **Actividades:** * Generación del proyecto base mediante Spring Initializr.
    * Organización de la estructura de paquetes: `controller`, `model`, `repository`.
    * Configuración del entorno de desarrollo en Visual Studio Code.
* **Logro:** Framework Spring Boot inicializado y corriendo localmente.

## Semana 2: Persistencia y Modelo de Datos
* **Actividades:** * Creación de tablas mediante sentencias DDL en SQL Server.
    * Definición de clases `@Entity` en Java con anotaciones JPA.
    * Configuración del archivo `application.properties` para vinculación con el motor de base de datos.
* **Logro:** Modelos ORM creados con mapeo correcto de llaves primarias.

## Semana 3: Conectividad y CRUD de Tablas Maestras
* **Actividades:** * **Resolución de conflictos de red:** Configuración de puertos y protocolos TCP/IP en SQL Server Configuration Manager.
    * **Gestión de Seguridad:** Habilitación de acceso SQL Server Authentication y configuración de credenciales de usuario.
    * **Desarrollo de API:** Creación de Repositorios e Interfaces para tablas `ROL`, `NIVEL` y `ESTADO`.
    * **Verificación:** Pruebas de endpoints REST mediante navegador, obteniendo respuestas en formato JSON.
* **Logro:** CRUD de lectura (Read) funcionando al 100% para todas las tablas maestras.

### Semana 3 - Finalización de Conexión y CRUD Maestro
* **Actividades:** * Configuración exitosa de protocolos TCP/IP en SQL Server.
    * Implementación de la entidad `Rol` y su mapeo ORM.
    * Creación del repositorio `RolRepository` extendiendo de JpaRepository.
    * Desarrollo del controlador `RolController` para exposición de datos vía API REST.
* **Resultado:** CRUD de tablas maestras funcionando y verificado mediante peticiones HTTP al puerto 8080.
------------------------------------------------------------------------------------------------------------------------------------------------------------------

# BITACORA DE DESARROLLO

## Proyecto: Plataforma Educativa - Spring Boot

---

# Entrada 1

## Fecha: 08/05/2026

Durante esta etapa se inició el análisis del proyecto y la construcción del modelo entidad relación (MER) de la plataforma educativa. Se definieron las tablas principales del sistema, incluyendo usuarios, roles, módulos, ejercicios, niveles y resultados.

También se realizó el análisis de relaciones entre tablas maestras y transaccionales para garantizar la integridad referencial en SQL Server.

### Actividades realizadas

* Diseño inicial del MER
* Definición de claves primarias y foráneas
* Creación de tablas maestras
* Planeación de arquitectura MVC

### Problemas encontrados

Se presentaron dudas en la relación entre las tablas transaccionales y las tablas maestras, especialmente en la tabla resultado.

### Solución aplicada

Se reorganizaron las relaciones utilizando claves foráneas para mantener la integridad de los datos.

### Uso de IA

Se utilizó IA como apoyo para validar relaciones y estructura inicial del modelo relacional.

---

# Entrada 2

## Fecha: 15/05/2026

En esta etapa se desarrolló la estructura backend utilizando Spring Boot, creando las entidades JPA, repositories y controllers para las tablas principales del sistema.

Además, se implementó el sistema de autenticación básica con inicio de sesión por roles.

### Actividades realizadas

* Creación de entidades JPA
* Implementación de repositories
* Implementación de controllers
* Configuración de conexión con SQL Server
* Desarrollo del login
* Validación de usuarios por rol

### Problemas encontrados

Se presentaron errores relacionados con las relaciones entre entidades y validaciones en Thymeleaf.

### Solución aplicada

Se corrigieron las anotaciones JPA y se reorganizaron las rutas de los controllers para mejorar la conexión entre frontend y backend.

### Uso de IA

Se utilizó IA para validar estructura de controladores, relaciones JPA y manejo de vistas Thymeleaf.

---

# Entrada 3

## Fecha: 22/05/2026

Se inició el desarrollo visual del sistema utilizando Thymeleaf y CSS. Se implementó el CRUD visual para la tabla maestra usuario y posteriormente para la tabla transaccional resultado.

También se desarrolló la lógica de redirección por roles.

### Actividades realizadas

* Desarrollo visual de usuarios
* Desarrollo visual de resultados
* Diseño CSS responsive
* CRUD visual
* Integración frontend y backend
* Registro automático de estudiantes
* Fecha automática en resultados

### Problemas encontrados

Se presentaron errores de conexión entre Thymeleaf y los modelos enviados desde los controllers.

### Solución aplicada

Se corrigieron los atributos enviados mediante Model y se reorganizaron las rutas de acceso a las vistas.

### Uso de IA

Se utilizó IA como apoyo para mejorar estilos visuales, corregir errores de Thymeleaf y optimizar la estructura visual del sistema.

---

# Entrada 4

## Fecha: 28/05/2026

Durante esta etapa final se realizaron pruebas generales del sistema, validando el funcionamiento del login, los roles, el CRUD visual y las relaciones entre tablas.

Además, se realizó documentación técnica del proyecto mediante README, bitácora y decisiones técnicas.

### Actividades realizadas

* Pruebas funcionales del sistema
* Validación de roles administrador y estudiante
* Verificación de persistencia en SQL Server
* Mejoras visuales del sistema
* Organización del proyecto
* Documentación técnica

### Problemas encontrados

Se detectaron inconvenientes relacionados con IDs manuales en algunas tablas y filtrado de usuarios por rol.

### Solución aplicada

Se analizaron mejoras futuras relacionadas con IDs autoincrementables y optimización de consultas JPA.

### Uso de IA

Se utilizó IA como apoyo para documentación técnica, mejora visual y validación de funcionalidades del sistema.
