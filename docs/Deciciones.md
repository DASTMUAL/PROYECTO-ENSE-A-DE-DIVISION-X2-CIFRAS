# Registro de Decisiones Arquitectónicas (ADR) - Plataforma Educativa


# Registro de Decisiones Arquitectónicas

## 1. Elección del Motor de Base de Datos
**Decisión:** Se optó por utilizar **Microsoft SQL Server**.
**Sustentación:** Debido a su robustez en entornos empresariales y su excelente integración con el ecosistema de Java a través de drivers JDBC oficiales. Además, permite un manejo eficiente de procedimientos almacenados y disparadores para futuras fases del proyecto.

## 2. Implementación de Arquitectura por Capas
**Decisión:** Se implementó un patrón de diseño basado en **capas (Controller, Repository, Model)**.
**Sustentación:** Esta separación de responsabilidades facilita el mantenimiento del código. La lógica de acceso a datos queda aislada en los Repositorios, mientras que la exposición de servicios se maneja en los Controladores, permitiendo que el framework Spring Boot gestione el ciclo de vida de los objetos de manera eficiente.





## 1. Motor de Base de Datos y Driver de Conexión
**Decisión:** Uso de **Microsoft SQL Server 2022** y driver **JDBC (mssql-jdbc)**.
**Sustentación:** Se eligió por su capacidad para manejar integridad referencial compleja y su compatibilidad con entornos empresariales. Se tomó la decisión técnica de habilitar protocolos TCP/IP estáticos en el puerto 1433 para garantizar que el framework Spring Boot localice la instancia de forma determinista.

## 2. Gestión de Dependencias
**Decisión:** Uso de **Maven**.
**Sustentación:** Se seleccionó Maven para automatizar la descarga de librerías y la construcción del proyecto (Build). El archivo `pom.xml` centraliza las dependencias de Spring Data JPA, Spring Web y el driver de SQL Server, asegurando que el entorno sea replicable en otros equipos.

## 3. Mapeo Objeto-Relacional (ORM)
**Decisión:** Implementación de **Spring Data JPA / Hibernate**.
**Sustentación:** Para optimizar el tiempo de desarrollo, se decidió abstraer las consultas SQL manuales. Mediante el uso de `@Entity`, las tablas `ROL`, `NIVEL` y `ESTADO` se manejan como objetos Java, delegando a Hibernate la creación y actualización de esquemas.

## 4. Seguridad de Acceso a Datos
**Decisión:** Configuración de **Autenticación Mixta** y usuario de servicio.
**Sustentación:** Se descartó el uso de Autenticación de Windows para evitar problemas de permisos de sistema operativo. Se habilitó el usuario `sa` con una política de contraseñas específica para permitir que la aplicación se autentique de forma independiente.
