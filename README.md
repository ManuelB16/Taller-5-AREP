# CRUD de Gestión de Propiedades

Este proyecto consiste en el desarrollo de un sistema CRUD (**Crear, Leer, Actualizar y Eliminar**) orientado a la **administración de propiedades inmobiliarias**.  
El objetivo es ofrecer una aplicación web que permita manejar anuncios de propiedades de manera simple, rápida y eficiente.

---

## Funcionalidades

- **Crear propiedades**: Registrar nuevas propiedades con sus datos principales (dirección, precio, tamaño, descripción).  
- **Leer propiedades**: Visualizar el listado de propiedades disponibles y acceder al detalle de cada una.  
- **Actualizar propiedades**: Modificar los datos de un registro existente en caso de cambios.  
- **Eliminar propiedades**: Borrar aquellas propiedades que ya no estén disponibles.  

---

## Tecnologías Utilizadas

### Backend
- **Spring Boot** → Framework para la creación de servicios REST.
- **JPA/Hibernate** → Mapeo objeto-relacional para el acceso a la base de datos.
- **MySQL** → Base de datos relacional para almacenar la información.

### Frontend
- **HTML5** → Estructura de la aplicación web.  
- **CSS3** → Diseño y estilos visuales.  
- **JavaScript (AJAX / Fetch API)** → Lógica de interacción con la API y manejo dinámico del contenido.  

---

## Arquitectura del Proyecto

1. **Backend (Spring Boot)**
   - **Controladores**: Manejan las solicitudes HTTP y exponen los endpoints de la API REST.
   - **Entidades**: Representan las tablas de la base de datos.
   - **Repositorios**: Contienen las operaciones CRUD para el acceso a los datos.  

2. **Frontend (HTML, CSS, JavaScript)**
   - **HTML**: Define la estructura general de la interfaz.  
   - **CSS**: Aplica estilos y diseño responsivo para mejorar la experiencia de usuario.  
   - **JavaScript**: Gestiona la lógica del cliente y la comunicación con el backend a través de llamadas REST (AJAX/Fetch API).  

---

## Despliegue

- La aplicación está diseñada para ejecutarse localmente contra una base de datos **MySQL**.  
- Puede desplegarse en **AWS** (usando instancias EC2 para el backend y RDS para la base de datos).  
- El frontend puede alojarse en un bucket **S3** con hosting estático o dentro de la aplicación backend.  

---

## Descripción de la Aplicación  

Esta aplicación web permite a los usuarios **registrar, visualizar, actualizar y eliminar propiedades inmobiliarias**.  
El proyecto está construido con **Spring Boot** en el backend y **HTML, CSS y JavaScript** en el frontend, utilizando **MySQL** como base de datos para el almacenamiento de la información.  

Este desarrollo ofrece experiencia práctica en:  
- Programación **Full-Stack**  
- Diseño e implementación de **APIs REST**  
- Integración con **bases de datos relacionales**  

---

### Usuario (User)  
El acceso al sistema se realiza mediante un navegador web (Browser) ingresando la siguiente URL:  

localhost:8081

---

### Recursos del Servidor  
El servidor está preparado para gestionar **múltiples solicitudes concurrentes** y administrar de forma eficiente los recursos necesarios para procesarlas.

---

## Descripción de las Clases  

### 1. **Property (Entidad Principal)**  
Representa la entidad **Propiedad Inmobiliaria**, con los siguientes atributos:  

- `id: Long` → Identificador único de la propiedad.  
- `address: String` → Dirección de la propiedad.  
- `price: String` → Precio de la propiedad.  
- `size: String` → Tamaño de la propiedad (m²).  
- `description: String` → Descripción breve de la propiedad.  

Incluye los **métodos getters y setters** para manipular dichos atributos.

---

### 2. **PropertyController (Controlador REST)**  
Expone los **endpoints REST** y maneja las operaciones CRUD.  

Métodos principales:
- `createProperty(property: Property): Property` → Crear una nueva propiedad.  
- `getAllProperties(): List<Property>` → Listar todas las propiedades.  
- `getPropertyById(id: Long): ResponseEntity<Property>` → Obtener una propiedad por su ID.  
- `updateProperty(id: Long, propertyDetails: Property): ResponseEntity<Property>` → Actualizar los datos de una propiedad.  
- `deleteProperty(id: Long): ResponseEntity<Void>` → Eliminar una propiedad existente.  

Este controlador utiliza **PropertyRepository** para conectarse con la capa de persistencia.

---

### 3. **PropertyRepository (Repositorio JPA)**  
Interfaz que extiende de `JpaRepository<Property, Long>`.  
Permite realizar operaciones CRUD sobre la base de datos de manera automática, utilizando la entidad `Property`.

---

### 4. **JpaRepository<Property, Long>**  
Interfaz genérica de Spring Data JPA.  
- La clase `Property` representa la entidad.  
- El parámetro `Long` corresponde al tipo de la clave primaria.  

Proporciona métodos estándar como:  
- `save()`  
- `findById()`  
- `findAll()`  
- `deleteById()`  

---

### 5. **ResponseEntity<T>**  
Clase utilizada para encapsular las **respuestas HTTP** del controlador.  

Ejemplos:
- `ResponseEntity<Property>` → Retorna una propiedad y el código de estado HTTP.  
- `ResponseEntity<Void>` → Retorna solo el código HTTP, usado en operaciones como **DELETE**.  

---

## 🔗 Relaciones entre las Clases  

- **PropertyController** usa **PropertyRepository** para acceder y manipular datos dentro de la base de datos.  
- **PropertyRepository** extiende de **JpaRepository**, lo que evita implementar consultas manualmente.  
- **ResponseEntity** asegura que las respuestas del backend tengan un formato adecuado y consistente en la API REST.

## Comenzando

Las siguientes instrucciones le permitirán obtener una copia del proyecto en funcionamiento en su máquina local para fines de desarrollo y prueba.

### Tecnologías usadas ⚙️

* [Maven](https://maven.apache.org/) : Gestor de dependencias y automatización de construcción para Java.
* [JavaScript](https://nodejs.org/) : Lenguaje de programación para interactividad en la web.
* [Java](https://www.java.com/es/) : Lenguaje de programación robusto para backend y aplicaciones empresariales.
* [SpringBoot](https://spring.io) : Marco web de Java basado en microservicios de código abierto que ofrece Spring.

```
* Versión Maven: 3.9.9
* Versión Java: 17
```

### Instalación

Realice los siguientes pasos para clonar el proyecto en su máquina local.

```
git clone https://github.com/ManuelB16/Taller-5-AREP
cd Taller-5-AREP
mvn clean compile
```

### Ejecutando la aplicación ⚙️

Para ejecutar la aplicación, ejecute el siguiente comando:

```
mvn exec:java -Dexec.mainClass="com.example.Application"

```

El anterior comando limpiará las contrucciones previas, compilará y empaquetará el código en un jar y luego ejecutará la aplicación.

Diríjase a su navegador de preferencia y vaya a la siguiente dirección: localhost:8081 para ver la aplicación en funcionamiento.

## Ejecutando las pruebas ⚙️

Para ejecutar las pruebas, ejecute el siguiente comando:

Las pruebas realizadas en este proyecto se enfocan en la validación y verificación de requisitos relacionados con el proceso de gestión de solicitudes, asegurando su correcto funcionamiento y cumplimiento de especificaciones.

```
mvn test
```
<img width="1268" height="413" alt="image" src="https://github.com/user-attachments/assets/ce5900b0-d06f-4023-8f25-3e23b0c13dcd" />


## Descripción de las pruebas

1. testCreateProperty (Prueba de Creación de Propiedad)
Descripción:

Simula una solicitud POST a /properties para crear una nueva propiedad.
Envía un JSON con los datos de la propiedad.
Verifica que la respuesta tenga un estado 200 OK.
Valida que los datos de la respuesta sean los mismos que los enviados (dirección, precio, tamaño y descripción).

2. testGetPropertyById (Prueba de Consulta por ID)
Descripción:

Crea y guarda una propiedad en la base de datos usando PropertyRepository.
Simula una solicitud GET a /properties/{id} para recuperar la propiedad creada.
Verifica que la respuesta tenga un estado 200 OK.
Confirma que los datos obtenidos coincidan con los de la propiedad almacenada.

3. testUpdateProperty (Prueba de Actualización de Propiedad)
Descripción:

Crea y guarda una propiedad en la base de datos.
Simula una solicitud PUT a /properties/{id} con nuevos valores para actualizar la propiedad.
Verifica que la respuesta tenga un estado 200 OK.
Confirma que los datos de la propiedad fueron actualizados correctamente en la respuesta.

4. testDeleteProperty (Prueba de Eliminación de Propiedad)
Descripción:

Crea y guarda una propiedad en la base de datos.
Simula una solicitud DELETE a /properties/{id} para eliminar la propiedad.
Verifica que la respuesta tenga un estado 204 No Content, lo que indica que la propiedad fue eliminada con éxito.

## Características principales: ⚙️

1. Interfaz moderna y responsiva:

* Un diseño minimalista con un esquema de colores que incluye degradados de tonos morados, creando una experiencia visual sofisticada.
* Totalmente adaptable a diferentes dispositivos gracias a su diseño responsivo.
* Panel de busqueda de archivos, el cual permite leer cualquier tipo de archivo localmente.
  
2. Gestión de archivos:

* Incluye botones interactivos que permiten abrir y visualizar archivos clave como:
* Ver las propiedades
* Agregar propiedades
* Archivos JavaScript (script.js).
* Hojas de estilo CSS (estilos.css).
* Documentos HTML (index.html).
* Imágenes (Chill.jpg).

## Muestra de la aplicación

https://drive.google.com/drive/u/0/folders/1wFPyNBLdCCwlJlTWCd96tmriSVujdRya

## Autor

Manuel Felipe Barrera Barrera

## Agradecimientos

Al profesor Daniel Benavides por su guia durante este desarrollo.

# NOTA

Se presentaron problemas con AWS (creditos insuficientes), asi que se opto por presentarse con un entorno local, la unica diferencia fundamental fue la subida del servidor, todo lo demas funciona como se espera.
