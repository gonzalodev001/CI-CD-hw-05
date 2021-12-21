# ENTREGABLE 5 - CI/CD
___

### Tecnologías utilizadas para la fase de Continuous Integration

- Nginx es un servidor proxy inverso de código abierto para los protocolos HTTP, HTTPS, así como un equilibrador de carga, caché HTTP y un servidor web.

- Symfony es un framework PHP con un conmjunto de componentes reutilizables, para proyectos web.

- PhpUnit permite realiaar test unitarios 

-Behat: es un marco php que le permite escribir test funcionales, escenarios de prueba para los endpoints de la aplicación

- Mysql es un gestor de base de datos.

___

### Jenkins Pipeline

![Texto alternativo](/jenkins-pipeline.png)
    
    Fase CI 
 - EL primer paso "Git clone" clona el proyecto del repositorio github.
 - El segundo paso "Build app" se contruye el los contenedoros desde el docker-compose.yml
 - En el terecer paso "Preper app" copia la base de datos dentro del contenedor de mysql
 - El cuarto paso "Run testing" ejecuta los test unitarios y funcionales que componen la aplicacion.
 - El quinto paso "Push Realese image" se construye la imagen y se envia al repositorio de contenedores DockerHub.
 - El sexto paso "Deploy kubernetes" se realiza el despligue a kubernetes ejecutando los manifiesto deployments y sus servicios, en este caso divididos en tres manifiestos de deploy para cada tecnologia y sus tres servicios.