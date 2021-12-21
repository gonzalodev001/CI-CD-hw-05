# ENTREGABLE 5 - CI/CD
___

### Tecnologías utilizadas para la fase de Continuous Integration

- Nginx es un servidor proxy inverso de código abierto para los protocolos HTTP, HTTPS, así como un equilibrador de carga, caché HTTP y un servidor web.

- Symfony es un framework PHP con un conmjunto de componentes reutilizables, para proyectos web.

- PhpUnit permite realiaar test unitarios 

-Behat: es un marco php que le permite escribir test funcionales, escenarios de prueba para los endpoints de la aplicación

- Mysql es un gestor de base de datos.

Aplicación web que trata de una API todo-list desarrollado en symfony en construcción, y el endpoint healthCheck funcional, los archivos del entorno los encotramos de la siguiente manera, para los Dockerfiles y archivos de configuración tanto para nginx y php estan en la carpeta /docker, y el manifiesto docker-componse.yml en la raiz del proyecto, para los manifiestos de kubernetes se encuentran en la carpeta /kubernetes se encuentran los de deploy y sus servicios. 
___

### Jenkins Pipeline

![Texto alternativo](/jenkins-pipeline.png)
    
#### Fase CI 
 - EL primer paso "Git clone" clona el proyecto del repositorio github.
 - El segundo paso "Build app" se contruye el los contenedoros desde el docker-compose.yml
 - En el terecer paso "Preper app" copia la base de datos dentro del contenedor de mysql
 - El cuarto paso "Run testing" ejecuta los test unitarios y funcionales que componen la aplicacion.

 #### Fase CD
 - El quinto paso "Push Realese image" se construye la imagen y se envia al repositorio de contenedores DockerHub.
 - El sexto paso "Deploy kubernetes" se realiza el despligue a kubernetes ejecutando los manifiesto deployments y sus servicios, en este caso divididos en tres manifiestos de deploy para cada tecnologia y sus tres servicios.