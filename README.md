# Sistema Administrativo Filey — MVC + Base de Datos (JDBC)
# PD


Enviar el URL donde se encuentra esta actividad que incluya:
Documentación de lo implementado
Código
Uso de patrón MVC + BD
Diagrama de clases
Diagrama de Entidad-Relación (Stands, Editorial y Reservación.)
Implementar JDBC para hacer lecturas de las Entidades Stands, Editorial y Reservación.
El main() debe mostrar que es posible la conexión a la BD y presentar las listas de cada tabla de Stands, Editorial y Reservación.
Video que explique el código para la lectura de las tablas Stands, Editorial y Reservación presentando el detalle de las capas. Uso del patrón MCV + capa de BDVideo de máximo 5 minutos. Incluir el URL en el repo (asegurar que hay acceso)
Completar el CRUD: Implementar el resto de las operaciones (Altas/Create, Bajas/Delete, Modificaciones/Update) para cada una de las entidades/tablas. 
Estrategias de Diseño a Evaluar: Al estructurar las operaciones de la base de datos y los controladores, se debe decidir y argumentar una estrategia (por ejemplo: juntar todas las operaciones iguales, o crear una clase y un controlador por entidad/tabla). 
Manejo de Excepciones:
Incluir un paquete de excepciones para errores lógicos o de validación (ej. intentar registrar un ID duplicado, borrar o actualizar algo que no existe, o conflictos en reservaciones cruzadas). 
Decidir con argumentos en qué capa (modelo, base de datos o controladores) deben vivir y lanzarse estas excepciones. 


# Video
https://alumnosuady-my.sharepoint.com/:v:/g/personal/a25216423_alumnos_uady_mx/IQBR29A8j6n0Rqz2RvA-GFXlAdY1VAXC126X19nnEqqHyxY?e=Hichq6

# Requisitos

Requisitos Funcionales (RF)

RF-01. Gestión de Conexión a Base de Datos: El sistema debe establecer y validar una conexión activa con la base de datos relacional (H2) mediante JDBC utilizando parámetros externalizados en db.properties y gestionados a través de ConexionBD y Configuracion.

RF-02. Gestión de Stands: El sistema debe permitir consultar, listar, registrar y actualizar stands y su estado (EstadoStand), reconstruyendo instancias de Stand desde la base de datos mediante StandDAO y StandController.

RF-03. Gestión de Editoriales: El sistema debe permitir consultar, registrar y administrar editoriales en la base de datos y mapearlas a objetos Editorial mediante EditorialDAO y EditorialController.

RF-04. Gestión de Reservaciones: El sistema debe permitir crear y administrar reservaciones de stands, validando reglas de negocio y conflictos de disponibilidad/asignación, y vinculando las entidades Reservacion, Stand y Editorial mediante ReservacionDAO, ReservacionController y ConflictoReservacionException.

RF-05. Procesamiento y Lógica de Negocio en Controladores: El sistema debe delegar la lógica operativa y validaciones a las clases del paquete controlador (StandController, EditorialController, ReservacionController y NotificacionController), manteniendo las clases del paquete modelo enfocadas en los datos/estado del dominio.

RF-06. Gestión de Notificaciones a Editoriales: El sistema debe contar con NotificacionController para procesar y emitir notificaciones o avisos vinculados a las operaciones o reservaciones de las editoriales.

RF-07. Inicialización y Carga de Esquema SQL: El sistema debe ejecutar scripts SQL (schema.sql y datos.sql) mediante InicializadorBD para crear la estructura de tablas y cargar los datos iniciales en la base de datos.

RF-08. Interacción y Visualización en Consola: Al ejecutar Main.java, el sistema debe inicializar la base de datos y presentar un menú interactivo en consola (ConsolaVista) para consultar registros (stands, editoriales, reservaciones) y ejecutar operaciones del sistema mostrando resultados y mensajes de error.

RF-09. Manejo de Excepciones del Dominio: El sistema debe controlar errores operativos y de datos mediante excepciones específicas en el paquete excepciones (FileyException, ValidacionException, RegistroDuplicadoException, RegistroNoEncontradoException y ConflictoReservacionException).

Requisitos No Funcionales (RNF)

RNF-01. Arquitectura en Capas (MVC / DAO / Excepciones): El código fuente debe mantenerse organizado en paquetes diferenciados: modelo, vista, controlador, bd y excepciones, separando presentación, lógica de negocio, acceso a datos y manejo de errores.

RNF-02. Desacoplamiento mediante Patrón DAO: El acceso a datos debe encapsularse en clases DAO (StandDAO, EditorialDAO, ReservacionDAO) para aislar las sentencias SQL y el manejo de JDBC del resto de las capas.

RNF-03. Estándar de Conectividad JDBC: La persistencia debe implementarse mediante JDBC sobre H2, con configuración desacoplada en db.properties y scripts SQL externos (schema.sql y datos.sql).

RNF-04. Externalización de Configuración y Credenciales: Los parámetros de conexión y configuración del sistema no deben ir fijos dentro de la lógica de negocio, sino externalizados en db.properties y leídos mediante Configuracion / ConexionBD.

RNF-05. Integridad de Recursos de Base de Datos: El sistema debe cerrar adecuadamente conexiones, sentencias y resultados tras las operaciones JDBC para prevenir fugas de recursos o bloqueos de conexión.

RNF-06. Mantenibilidad y Documentación Técnica: El repositorio debe incluir documentación en README.md y diagramas actualizados en docs/ (diagrama_clases.png/diagrama_clases.dot y diagrama_er.png/diagrama_er.dot) acordes con el modelo y la base de datos.

RNF-07. Compatibilidad de Entorno y Gestión de Dependencias: El proyecto debe gestionarse con Apache Maven (pom.xml) para resolver dependencias (como el driver de H2) y compilar/ejecutar de forma reproducible en Visual Studio Code.

RNF-08. Coherencia de Tipos de Datos entre SQL y Java: El esquema relacional en schema.sql debe utilizar tipos de datos compatibles con los atributos de las entidades en Java para evitar pérdidas de información o errores de mapeo.


# Diagrama-Clases 
<img width="3725" height="1172" alt="diagrama_clases" src="https://github.com/user-attachments/assets/bbde4175-8ae7-47ad-aa50-4162833c13c7" />

# Diagrama Relacion-Entidad
<img width="861" height="426" alt="diagrama_er" src="https://github.com/user-attachments/assets/77eaf9c7-d840-4585-9243-6487cf08fc9f" />

