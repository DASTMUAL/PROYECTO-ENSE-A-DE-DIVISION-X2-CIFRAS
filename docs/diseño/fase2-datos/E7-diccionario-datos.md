# 📂 Documentación del Proyecto - Plataforma Educativa

## FASE 2 -> Capa de Datos (Diccionario de Datos)

Esta sección describe la estructura lógica de la base de datos, detallando cómo cada entidad se traduce en tablas físicas dentro de **SQL Server** y su impacto en el framework de Spring Boot.

### Resumen de Entidades
| Entidad de Datos | Lo que genera en el Framework |
| :--- | :--- |
| `USUARIO` | Centraliza la persistencia de perfiles, credenciales y vinculación con roles y estados. |
| `ROL` | Define los niveles de acceso y permisos (`estudiante`, `administrador`) para la seguridad. |
| `ESTADO_USUARIO` | Controla la disponibilidad del acceso mediante estados maestros (`Activo`, `Inactivo`). |
| `CURSO` | Almacena la oferta educativa principal disponible en la plataforma. |
| `MODULO` | Organiza los grupos de ejercicios por temáticas específicas dentro de cada curso. |
| `NIVEL` | Gestiona la dificultad y el puntaje estándar para la gamificación del sistema. |
| `EJERCICIO` | Representa la unidad básica de interacción pedagógica y evaluación. |
| `OPCION_RESPUESTA` | Almacena las alternativas de respuesta y la validación de la solución correcta. |
| `RESULTADO` | Registra el histórico de intentos y desempeño individual de cada estudiante. |
| `PROGRESO` | Mapea el avance porcentual y temporal del usuario por cada módulo. |
| `INSIGNIA` | Entidad de reconocimiento para logros visuales obtenidos por objetivos cumplidos. |
| `USUARIO_INSIGNIA` | Tabla relacional que vincula los logros obtenidos con el perfil del estudiante. |

---

### Detalle de Estructura por Tabla

#### 1. `USUARIO`
**Descripción:** Almacena la información de ingreso y perfil del usuario.

| Campo | Tipo de Dato | Tamaño | Nulo | PK/FK | Descripción |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `id_usuario` | `INT` | 10 | NO | **PK** | Identificador único del usuario. |
| `nombre` | `VARCHAR` | 100 | NO | - | Nombre completo del usuario. |
| `identificacion` | `VARCHAR` | 20 | SÍ | - | Documento de identidad. |
| `correo` | `VARCHAR` | 100 | NO | - | Correo para login. |
| `telefono` | `VARCHAR` | 10 | NO | - | Teléfono de contacto. |
| `contraseña` | `VARCHAR` | 255 | NO | - | Contraseña encriptada. |
| `id_rol` | `INT` | 10 | NO | **FK** | Referencia a tabla `ROL`. |
| `id_estado` | `INT` | 10 | NO | **FK** | Referencia a `ESTADO_USUARIO`. |

#### 2. `ROL`
**Descripción:** Define los tipos de acceso al sistema.

| Campo | Tipo | Tamaño | Nulo | PK/FK | Descripción |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `id_rol` | `INT` | 10 | NO | **PK** | ID del rol. |
| `nombre` | `VARCHAR` | 50 | NO | - | Nombre del rol (ej: estudiante, administrador). |

#### 3. `ESTADO_USUARIO`
**Descripción:** Centraliza los estados permitidos.

| Campo | Tipo | Tamaño | Nulo | PK/FK | Descripción |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `id_estado` | `INT` | 10 | NO | **PK** | ID del estado. |
| `nombre_estado` | `VARCHAR` | 25 | NO | - | Ej: Activo, Inactivo. |

#### 4. `CURSO`
**Descripción:** Información general de los cursos.

| Campo | Tipo | Tamaño | Nulo | PK/FK | Descripción |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `id_curso` | `INT` | 10 | NO | **PK** | ID del curso. |
| `nombre` | `VARCHAR` | 100 | NO | - | Nombre del curso educativo. |
| `descripcion` | `VARCHAR` | 255 | NO | - | Detalle del contenido. |

#### 5. `MODULO`
**Descripción:** Agrupación temática de ejercicios.

| Campo | Tipo | Tamaño | Nulo | PK/FK | Descripción |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `id_modulo` | `INT` | 10 | NO | **PK** | ID del módulo. |
| `nombre` | `VARCHAR` | 100 | NO | - | Nombre del módulo. |
| `id_curso` | `INT` | 10 | NO | **FK** | Referencia al curso contenedor. |

#### 6. `NIVEL`
**Descripción:** Define la dificultad y puntaje.

| Campo | Tipo | Tamaño | Nulo | PK/FK | Descripción |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `id_nivel` | `INT` | 10 | NO | **PK** | ID del nivel de dificultad. |
| `nombre` | `VARCHAR` | 25 | NO | - | Ej: Básico, Intermedio, Avanzado. |
| `puntaje_nivel` | `INT` | 10 | NO | - | Puntaje otorgado al nivel. |

#### 7. `EJERCICIO`
**Descripción:** Problemas académicos a resolver.

| Campo | Tipo | Tamaño | Nulo | PK/FK | Descripción |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `id_ejercicio` | `INT` | 10 | NO | **PK** | ID del ejercicio. |
| `enunciado` | `VARCHAR` | 50 | NO | - | El problema matemático. |
| `id_nivel` | `INT` | 10 | NO | **FK** | Dificultad asociada. |
| `id_modulo` | `INT` | 10 | NO | **FK** | Módulo de pertenencia. |

#### 8. `OPCION_RESPUESTA`
**Descripción:** Alternativas de solución.

| Campo | Tipo | Tamaño | Nulo | PK/FK | Descripción |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `id_opcion` | `INT` | 10 | NO | **PK** | ID de la opción. |
| `id_ejercicio` | `INT` | 10 | NO | **FK** | Referencia al ejercicio. |
| `respuesta_opcion` | `INT` | 3 | NO | - | Valor de la respuesta. |
| `es_correcta` | `BOOLEAN` | - | NO | - | Validación lógica (Correcto/Incorrecto). |

#### 9. `RESULTADO`
**Descripción:** Registro de intentos del usuario.

| Campo | Tipo | Tamaño | Nulo | PK/FK | Descripción |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `id_resultado` | `INT` | 10 | NO | **PK** | ID único del intento. |
| `id_usuario` | `INT` | 10 | NO | **FK** | Estudiante ejecutor. |
| `id_ejercicio` | `INT` | 10 | NO | **FK** | Ejercicio realizado. |
| `respuesta_usuario` | `INT` | 3 | NO | - | Valor ingresado. |
| `fecha` | `DATETIME` | - | NO | - | Momento de la respuesta. |

#### 10. `PROGRESO`
**Descripción:** Seguimiento del avance del usuario.

| Campo | Tipo | Tamaño | Nulo | PK/FK | Descripción |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `id_progreso` | `INT` | 10 | NO | **PK** | ID del progreso. |
| `id_usuario` | `INT` | 10 | NO | **FK** | Usuario vinculado. |
| `id_modulo` | `INT` | 10 | NO | **FK** | Módulo evaluado. |
| `fecha_actualizacion` | `DATETIME` | - | NO | - | Último registro de avance. |

#### 11. `INSIGNIA`
**Descripción:** Logros visuales.

| Campo | Tipo | Tamaño | Nulo | PK/FK | Descripción |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `id_insignia` | `INT` | 10 | NO | **PK** | ID de la medalla. |
| `nombre` | `VARCHAR` | 50 | NO | - | Nombre del logro. |

#### 12. `USUARIO_INSIGNIA`
**Descripción:** Relación de medallas obtenidas.

| Campo | Tipo | Tamaño | Nulo | PK/FK | Descripción |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `id_usuario_insignia` | `INT` | 10 | NO | **PK** | ID de obtención. |
| `id_usuario` | `INT` | 10 | NO | **FK** | Ganador de la medalla. |
| `id_insignia` | `INT` | 10 | NO | **FK** | Medalla otorgada. |
| `fecha_obtenida` | `DATETIME` | - | NO | - | Fecha de premio. |

























________________________________________
DICCIONARIO DE DATOS - PLATAFORMA EDUCATIVA 
1.	TABLA: ROL Descripción: Define los tipos de usuario y sus niveles de acceso dentro del sistema. 
•	id_rol (PK): INT(10) | No Nulo | PK | Identificador único de cada rol. 
•	nombre (único): VARCHAR(50) | No Nulo | Nombre del rol (ej: estudiante, administrador). 
________________________________________
2.	TABLA: ESTADO_USUARIO Descripción: Centraliza los estados permitidos para los usuarios. 
•	id_estado (PK): INT(10) | No Nulo | PK | Identificador único del estado. 
•	nombre_estado: VARCHAR(25) | No Nulo | Nombre del estado (Activo/Inactivo). 
________________________________________
3.	TABLA: CURSO Descripción: Almacena la información de los cursos disponibles. 
•	id_curso (PK): INT(10) | No Nulo | PK | Identificador único del curso. 
•	nombre: VARCHAR(100) | No Nulo | Nombre del curso. 
•	descripcion: VARCHAR(255) | No Nulo | Descripción del curso. 
________________________________________
4.	TABLA: NIVEL Descripción: Define los grados de dificultad y centraliza el puntaje. 
•	id_nivel (PK): INT(10) | No Nulo | PK | Identificador único del nivel. 
•	nombre: VARCHAR(25) | No Nulo | Nombre del nivel (ej: Básico, Intermedio). 
•	descripcion: VARCHAR(50) | Nulo | Descripción del nivel. 
•	puntaje_nivel: INT(10) | No Nulo | Puntaje fijo asignado a este nivel. 
________________________________________
5.	TABLA: INSIGNIA Descripción: Almacena los reconocimientos visuales o logros obtenidos. 
•	id_insignia (PK): INT(10) | No Nulo | PK | Identificador de la insignia. 
•	nombre: VARCHAR(50) | No Nulo | Nombre de la insignia. 
________________________________________
6.	TABLA: USUARIO Descripción: Información personal y credenciales de acceso. 
•	id_usuario (PK): INT(10) | No Nulo | PK | Identificador único del usuario. 
•	nombre: VARCHAR(100) | No Nulo | Nombre completo del usuario. 
•	identificacion: VARCHAR(20) | Nulo | Identificación del usuario. 
•	correo: VARCHAR(100) | No Nulo | Correo electrónico para login. 
•	telefono: VARCHAR(10) | No Nulo | Teléfono de contacto. 
•	contraseña: VARCHAR(255) | No Nulo | Contraseña del usuario. 
•	id_rol (FK): INT(10) | No Nulo | FK (ROL) | Referencia al rol del usuario. 
•	id_estado (FK): INT(10) | No Nulo | FK (ESTADO_USUARIO) | Referencia al estado. 
________________________________________
7.	TABLA: MODULO Descripción: Contiene la agrupación de ejercicios por curso. 
•	id_modulo (PK): INT(10) | No Nulo | PK | Identificador único del módulo. 
•	nombre: VARCHAR(100) | No Nulo | Nombre del módulo. 
•	id_curso (FK): INT(10) | No Nulo | FK (CURSO) | Curso al que pertenece. 
________________________________________
8.	TABLA: EJERCICIO Descripción: Contiene los enunciados y la información de las actividades. 
•	id_ejercicio (PK): INT(10) | No Nulo | PK | Identificador único del ejercicio. 
•	enunciado: VARCHAR(50) | No Nulo | Descripción del problema. 
•	id_nivel (FK): INT(10) | No Nulo | FK (NIVEL) | Nivel de dificultad. 
•	estado: BOOLEAN | No Nulo | Indica si el ejercicio está activo. 
•	id_modulo (FK): INT(10) | No Nulo | FK (MODULO) | Módulo asociado. 
________________________________________
9.	TABLA: OPCION_RESPUESTA Descripción: Alternativas de respuesta para cada ejercicio. 
•	id_opcion (PK): INT(10) | No Nulo | PK | Identificador de la opción. 
•	id_ejercicio (FK): INT(10) | No Nulo | FK (EJERCICIO) | Ejercicio asociado. 
•	respuesta_opcion: INT(3) | No Nulo | Valor de la respuesta. 
•	es_correcta: BOOLEAN | No Nulo | Define si la opción es la válida. 
________________________________________
10.	TABLA: RESULTADO Descripción: Registro de los intentos realizados por los estudiantes. 
•	id_resultado (PK): INT(10) | No Nulo | PK | Identificador del resultado. 
•	id_usuario (FK): INT(10) | No Nulo | FK (USUARIO) | Usuario que realizó el intento. 
•	id_ejercicio (FK): INT(10) | No Nulo | FK (EJERCICIO) | Ejercicio evaluado. 
•	respuesta_usuario: INT(3) | No Nulo | Respuesta dada por el usuario. 
•	fecha: DATETIME | No Nulo | Fecha y hora del intento. 
________________________________________
11.	TABLA: PROGRESO Descripción: Registra el avance del estudiante por módulo. 
•	id_progreso (PK): INT(10) | No Nulo | PK | Identificador del progreso. 
•	id_usuario (FK): INT(10) | No Nulo | FK (USUARIO) | Usuario asociado. 
•	id_modulo (FK): INT(10) | No Nulo | FK (MODULO) | Módulo evaluado. 
•	fecha_actualizacion: DATETIME | No Nulo | Fecha de última actualización. 
________________________________________
12.	TABLA: USUARIO_INSIGNIA Descripción: Vincula a los usuarios con las insignias obtenidas. 
•	id_usuario_insignia (PK): INT(10) | No Nulo | PK | Identificador del registro. 
•	id_usuario (FK): INT(10) | No Nulo | FK (USUARIO) | Estudiante premiado. 
•	id_insignia (FK): INT(10) | No Nulo | FK (INSIGNIA) | Insignia ganada. 
•	fecha_optenida: DATETIME | No Nulo | Fecha de obtención. 

