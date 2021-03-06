## Descripción
Platzi - Curso de Hibernate y Java Spring - App Spring Boot

## Docker - Instalación y ejecución
1. Descargar la imagen de postgres.
<br>`docker pull postgres:9.6.6-alpine`
2. Ejecutar la imagen para crear el contenedor.
<br>`docker run -d --name postgres -p 5432:5432 -e POSTGRES_PASSWORD=platzi postgres:9.6.6-alpine`
3. Iniciar el contenedor ya existente (si está abajo).
<br>`docker start postgres`
- Ver el estado de los contenedores actuales.
<br>`docker ps -a`
- Eliminar un contenedor de manera forzada.
<br>`docker rm -f postgres`
4. Construir imagen en docker por medio del pom.xml.
<br>`mvn clean install docker:build`
5. Subir la imagen a Docker Hub.
<br>`docker login` y `docker push revol89/e-reservation`
6. Crear un contenedor a través de nuestra imagen generada (postgres_server será la ip del equipo local).
<br>`docker run -d --name ereservation --add-host=postgres_server:192.168.206.128 -p 8080:8080 revol89/e-reservation:latest`
- Visualizar el log del contenedor creado.
<br>`docker logs -f ereservation`
- Detener y reiniciar el contenedor.
<br>`docker stop ereservation` y `docker restart ereservation`
- Eliminar una imagen de Docker.
<br>`docker rmi revol89/e-reservation`

## Proyecto Spring Boot.
- Se debe instalar el Plugin de [Lombok](http://www.advlatam.com/en/lombok-a-library-to-code-more-cleanly/) en IntelliJ IDEA para que tome las anotaciones AllArgsConstructor, Data, que tome los getters y setters, entre otros.
- El contenedor docker debe estar arriba antes de iniciar el proyecto de Spring Boot.
    > El lo que hará es que a través del archivo [**application.yaml**](https://github.com/cesardramirez/e-reservation/blob/master/src/main/resources/application.yaml#L9) es crear la base de datos por medio de Hibernate por primera vez a través de los modelos.
- La imagen de Docker quedará desplegada en [DockerHub](https://hub.docker.com/r/revol89/e-reservation).
<br>![](/docs/img_05.png)

## Swagger y Login.
- Se añade un modo de autenticación y permisos para ingresar al swagger.
- Se ingresa al [login](http://localhost:8080/app/login) con el usuario __cesar__ y la clave __platzi__.
<br>![](/docs/img_01.png)
- Si las credenciales no son las correctas, se le visualizará al usuario.
<br>![](/docs/img_02.png)
- Si su autenticación es exitosa, ingresará a la pantalla de [home](http://localhost:8080/app/home).
<br>![](/docs/img_03.png)
- Se visualizará correctamente la página construida para Swagger.
<br>![](/docs/img_04.png)