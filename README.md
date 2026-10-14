# API REST - Sistema de Alquiler de Apartamentos y Habitaciones

## Descripción del proyecto

Este proyecto consiste en el desarrollo de una API REST para la administración de un sistema de alquiler de apartamentos, habitaciones y otras unidades rentables.

La aplicación permite gestionar propiedades, clientes, unidades disponibles, reservas, pagos y otros elementos relacionados con el proceso de alojamiento.

El sistema fue desarrollado utilizando **Java, Spring Boot y MySQL**, siguiendo una arquitectura por capas para organizar los controladores, servicios, repositorios y modelos.

Además de los servicios REST, el proyecto incorpora una interfaz web administrativa desarrollada con **Thymeleaf, HTML y CSS**, que permite visualizar y administrar información desde el navegador.

## Objetivo

Desarrollar un sistema que facilite la administración de propiedades y unidades destinadas al alquiler, centralizando la información de clientes, reservas, disponibilidad y pagos mediante servicios REST.

## Tecnologías utilizadas

- **Java:** lenguaje de programación principal.
- **Spring Boot:** framework para el desarrollo de la aplicación.
- **Spring Web MVC:** implementación de controladores y servicios HTTP.
- **Spring Data JPA:** acceso y persistencia de datos.
- **Hibernate:** mapeo objeto-relacional.
- **MySQL:** sistema gestor de bases de datos.
- **Maven:** administración de dependencias.
- **Thymeleaf:** creación de vistas web dinámicas.
- **HTML y CSS:** diseño de la interfaz administrativa.
- **Postman:** pruebas de los servicios REST.
- **Git y GitHub:** control de versiones y alojamiento del código.

## Funcionalidades principales

El sistema contempla los siguientes módulos:

1. **Gestión de clientes:** registro, consulta y administración de información de los clientes.
2. **Gestión de propiedades:** registro y administración de inmuebles destinados al alquiler.
3. **Gestión de unidades rentables:** administración de apartamentos, habitaciones y otras unidades asociadas a una propiedad.
4. **Gestión de reservas:** registro y seguimiento de las reservas realizadas.
5. **Gestión de disponibilidad:** consulta y administración de la disponibilidad de unidades.
6. **Gestión de pagos:** registro y consulta de información relacionada con los pagos.
7. **Gestión de reseñas:** almacenamiento y administración de opiniones.
8. **Gestión de notificaciones:** administración de avisos relacionados con el sistema.
9. **Gestión de imágenes:** asociación de imágenes con las propiedades.

## Arquitectura del proyecto

La aplicación sigue una arquitectura por capas:

- **Models:** representan las entidades del sistema y sus relaciones.
- **Repositories:** permiten consultar y almacenar datos mediante JPA.
- **Services:** contienen las operaciones y reglas de negocio.
- **Controllers:** reciben las solicitudes HTTP y permiten acceder a las funcionalidades del sistema.
- **Templates:** contienen las páginas HTML utilizadas por la interfaz web.
- **Static:** almacena recursos como los archivos CSS.

Esta separación facilita el mantenimiento y la organización del código.

## Requisitos previos

Antes de ejecutar el proyecto es necesario contar con:

- Java compatible con la versión configurada en `pom.xml`.
- MySQL Server.
- Maven o Maven Wrapper.
- Un editor de código como Visual Studio Code.
- Postman para realizar las pruebas de la API.

## Instalación y ejecución

### 1. Clonar el repositorio

Abrir una terminal y ejecutar:

```bash
git clone https://github.com/ArturoUCC/API-APARTAMENTOS.git
```

Ingresar a la carpeta del proyecto:

```bash
cd API-APARTAMENTOS
```

### 2. Configurar la base de datos

Iniciar el servidor MySQL y crear la base de datos:

```sql
CREATE DATABASE IF NOT EXISTS apartamentos;
```

El proyecto utiliza Spring Data JPA y Hibernate para gestionar las entidades y sus tablas.

### 3. Configurar la conexión con MySQL

Abrir el archivo:

`src/main/resources/application.properties`

La configuración recomendada es:

```properties
spring.application.name=apartamentos

server.port=8000

spring.datasource.url=jdbc:mysql://localhost:3306/apartamentos?createDatabaseIfNotExist=true&useSSL=false&serverTimezone=UTC

spring.datasource.username=${DB_USERNAME:root}
spring.datasource.password=${DB_PASSWORD}

spring.jpa.hibernate.ddl-auto=update
spring.jpa.open-in-view=false
```

**Variables de entorno necesarias:**

| Variable | Descripción |
|---|---|
| `DB_USERNAME` | Usuario de MySQL. Su valor predeterminado es `root`. |
| `DB_PASSWORD` | Contraseña del usuario de MySQL. |

En Windows CMD se pueden establecer para la terminal actual mediante:

```cmd
set DB_USERNAME=root
set DB_PASSWORD=TU_CONTRASENA_LOCAL
```

No se recomienda publicar contraseñas reales en el repositorio.

### 4. Ejecutar el proyecto

En Windows, desde la carpeta principal del proyecto, ejecutar:

```cmd
mvnw.cmd spring-boot:run
```

También puede ejecutarse la clase principal `ApartamentosApplication.java` desde Visual Studio Code.

Si la aplicación inicia correctamente, el servidor estará disponible en:

**http://localhost:8000/**

## Servicios REST

El proyecto contiene controladores para las siguientes entidades y operaciones:

| Módulo | Función |
|---|---|
| Propiedades | Administración de inmuebles |
| Unidades rentables | Administración de habitaciones y apartamentos |
| Clientes | Administración de clientes |
| Reservas | Administración de reservas |
| Disponibilidad | Control de disponibilidad |
| Pagos | Administración de pagos |
| Reseñas | Administración de opiniones |
| Notificaciones | Administración de avisos |
| Imágenes de propiedades | Asociación de imágenes |

Los métodos HTTP utilizados por una API REST para operaciones CRUD incluyen:

| Método | Operación |
|---|---|
| `GET` | Consultar registros |
| `POST` | Crear registros |
| `PUT` | Actualizar registros |
| `DELETE` | Eliminar registros |

**Nota:** las rutas específicas de cada módulo deben consultarse en las anotaciones `@RequestMapping`, `@GetMapping`, `@PostMapping`, `@PutMapping` y `@DeleteMapping` de sus controladores.

## Ejemplos de solicitudes y respuestas

Los siguientes ejemplos muestran el formato general de intercambio de información en JSON. Los campos y rutas definitivos dependen de la implementación de cada controlador.

### Ejemplo 1. Solicitud para registrar una propiedad

**Método:** `POST`

**Cuerpo de solicitud ilustrativo:**

```json
{
  "titulo": "Apartamento en Veracruz",
  "ubicacion": "Veracruz, Veracruz",
  "precioNoche": 1200,
  "capacidad": 4
}
```

**Respuesta ilustrativa:**

```json
{
  "id": 1,
  "titulo": "Apartamento en Veracruz",
  "ubicacion": "Veracruz, Veracruz",
  "precioNoche": 1200,
  "capacidad": 4
}
```

### Ejemplo 2. Consulta de propiedades

**Método:** `GET`

**Respuesta ilustrativa:**

```json
[
  {
    "id": 1,
    "titulo": "Apartamento en Veracruz",
    "precioNoche": 1200
  }
]
```

Estos ejemplos son orientativos y deben ajustarse a los campos reales de los modelos y controladores antes de utilizarlos como evidencia de una prueba.

## Interfaz web administrativa

Además de los endpoints REST, la aplicación cuenta con una interfaz web desarrollada utilizando Thymeleaf.

Desde esta interfaz es posible navegar por las distintas secciones administrativas del sistema y visualizar información relacionada con los registros.

**Dirección de acceso local:**

http://localhost:8000/

## Pruebas con Postman

Para comprobar el funcionamiento de la API se utiliza Postman.

Las pruebas pueden abarcar:

1. Consulta de registros mediante `GET`.
2. Creación de registros mediante `POST`.
3. Actualización de información mediante `PUT`.
4. Eliminación de registros mediante `DELETE`.
5. Verificación de relaciones entre clientes, propiedades, unidades y reservas.

Las evidencias de las pruebas se documentan mediante capturas de pantalla de las solicitudes y respuestas HTTP.

## Repositorio

**GitHub:** https://github.com/ArturoUCC/API-APARTAMENTOS

## Autor

**Arturo Sebastián Peña Vázquez**

Proyecto académico desarrollado para la materia de Arquitectura Orientada a Servicios (SOA).

## Conclusión

Esta API REST permite organizar las operaciones principales de un sistema de alquiler de apartamentos y habitaciones mediante una aplicación desarrollada con Spring Boot y MySQL.

Su arquitectura por capas facilita la separación de responsabilidades entre los distintos componentes, mientras que la interfaz web y los servicios HTTP ofrecen dos formas de interactuar con la información del sistema.
