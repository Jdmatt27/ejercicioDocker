# ejercicioDocker

1. ¿Por qué el frontend no necesita conectarse a PostgreSQL?

    Solo habla con el backend por la API, y es el backend quien accede a la base de datos.

2. ¿Por qué el backend pertenece a dos redes?

    Hace de puente: recibe peticiones del frontend por una red y consulta la base de datos por la otra.

3. ¿Qué servicio necesita publicar un puerto en el anfitrión?

    El frontend, porque es el único al que accede el usuario desde fuera.

4. ¿Por qué publicar PostgreSQL hacia fuera no es la solución adecuada para un fallo de comunicación interno?

    El fallo es interno (redes, nombre db, credenciales). Publicar el puerto no lo arregla y además expone la base de datos.

5. ¿Qué ventaja ofrece Docker Compose respecto a ejecutar los tres contenedores manualmente?

    Toda la configuración está en un archivo y lo levantas o lo paras todo con un comando. Es reproducible y da menos errores.

6. ¿Por qué hemos dividido la arquitectura en dos redes?

    Por aislamiento y seguridad: el frontend no puede llegar a la base de datos.

7. ¿Por qué el backend utiliza `db` como dirección de PostgreSQL?

    El DNS interno de Docker traduce el nombre del servicio a la IP del contenedor, que puede cambiar.

8. ¿Qué diferencia existe entre detener un proyecto y eliminar sus volúmenes?

    stop o down paran el proyecto y conservan los datos. down -v borra los volúmenes y con ellos los datos.

9. ¿Qué consecuencias tendría para la empresa perder el volumen de PostgreSQL?

    Pierde todos los datos (clientes, pedidos…), con parada del servicio, pérdidas económicas y posibles problemas legales. Por eso hacen falta copias de seguridad.
