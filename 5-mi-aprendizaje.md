# COMPLETAR  
Comparando sus conocimientos antes de hacer la práctica con sus conocimientos después de hacer la tarea, explicar los principales aprendizajes logrados para beneficio de su formación profesional.  
Si solucionó un problema presentado al realizar la práctica también se debe documentar.
# ANTES DE LA PRÁCTICA
Una vez que, nos adentramos en el tema tenia solamente la idea muy superficial de lo que Docker desempeñaba. Por lo que, nunca habia configurado un mapeo de puertos o desplegado un servicio como RabbitMQ en un contenedor. 
# DESPUES DE LA PRÁCTICA
## Aprendizaje 
Aprendí los comandos mencionados en esta practica tales como:
1 docker pull <nombre imagen> 
2 docker pull <nombre imagen>:<tag>
3 docker inspect <nombre imagen>
4 docker inspect <nombre imagen>:<tag>
5 docker rmi <nombre imagen>:<tag>
6 docker create --name <nombre contenedor> <nombre imagen>:<tag>
7 docker ps -a
8 docker run --name <nombre contenedor> <nombre imagen>:<tag>
9 docker rm <nombre contenedor>
10 docker run -d --name <nombre contenedor> -p <puerto host>:<puerto contenedor> <nombre imagen>:<tag>
Aprendi a mapear correctamente los puertos entre host y el contenedor desde minavegador. Comprendí como utilizar las 
herramientas de Docker para gestionar contenedores y como RabbitMQ opera dentro de un contenedor con su panel de 
administracion web accesible a traves de un puerto especifico.
Los problemas que presente esque durante la practica me tope con puertos bloqueados, problemas al iniciar sesion en Docker 
al momento de instalarlo, no podia ingresar a la terminal del mismo pero intenté acceder a la interfaz de administración de 
RabbitMQ, ya que olvidé mapear correctamente el puerto 15672 en el host. Después de revisar la documentación de Docker, 
comprendí cómo utilizar correctamente el comando (docker run) con el parámetro -p para mapear los puertos de manera 
adecuada. Esto me ayudó a resolver el problema y acceder a la interfaz sin dificultades.
## Conclusión 
Me agradó mucho como fue detallando el documento de la practica, como se fueron desglosando los pasos para un mayor 
entendimiento, me gustó mucho el curso y sobretodo que aprendí.
