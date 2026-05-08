
### FASE 1 → Estructura del Proyecto

| Artefacto de Diseño | Lo que genera en el Framework |
| :--- | :--- |
| **E5 - Diagrama de Componentes** | [cite_start]Define la estructura de carpetas y paquetes del proyecto Spring Boot, organizando el código en `controller`, `model` y `repository`. |
| **E6 - Diagrama de Despliegue** | [cite_start]Establece la configuración del entorno en `application.properties`, incluyendo la conexión al puerto 8080/8081 y las variables para el servidor SQL Server. |
| **E4 - Arquetipos** | [cite_start]Determina los nombres de las clases de entidad (`Usuario`, `Rol`, `Nivel`, `Curso`), así como la estructura de los modelos y servicios RESTful. |

Artefacto de Diseño,Lo que genera en el Framework
E11 - Script DDL,"Creación física de las 12 tablas en SQL Server, definiendo tipos de datos, llaves primarias y foráneas para la persistencia .  "
E9-E10 - Modelo Relacional,"Estructura lógica que se traduce en clases @Entity de Java, permitiendo la comunicación entre el objeto y la tabla mediante JPA .  +2"
E7 - Diccionario de Datos,"Define las validaciones y restricciones técnicas (como @Column(nullable = false)) y tipos de variables (String, Integer) en los modelos .  +2"
E8 - MER,Determina la cardinalidad y lógica de las relaciones que se implementan en el código mediante anotaciones @ManyToOne y @OneToMany .  +1
