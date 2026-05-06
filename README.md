
 # #########1
# Paso 1

Voy a crear un contenedor que tendrá un Sistema operativo Ubuntu.

Entro en Docker → Docker Hub
Busco ubuntu 

Selecciono la imagen correspondiente

 
![1](Capturas/1.png)


y doy a Run

y le doy nombre al contenedor. (UbuntuMayo2026) . Pero ese contenedor no tiene los permisos apropiados, así que lo elimino.

![2](Capturas/2.png)

![3](Capturas/3.png)


Ahora doy al “Play” de la imagen Ubuntu que la sigo teniendo en Images.
Le pongo el nombre y en este caso no hay puertos que configurar.

![4](Capturas/4.png)

 
Ir a Containers y ejecutarlo si no esté ejecutado

Para acceder a la terminal del contenedor pinchamos en “Terminal”, abajo a la derecha

Ejecuto debug (Hará pull y se descarga la imagen)

![5](Capturas/5.png) 

![6](Capturas/6.png)

Ejecuto apt-get update e instalo curl

 ![7](Capturas/7.png)

Compruebo que funciona, con curl - -version

![8](Capturas/8.png)
 

Pregunta
¿Con qué comando podrías guardar los cambios del contenedor como una nueva imagen?
Con 
	“docker build - -tag ubuntu:v1 .”

 # Paso 2

Creo el fichero Dockerfile en el raíz de mi proyecto y copio los comandos para actualizar e instalar curl.


![9](Capturas/9.png)

Grabo el fichero y ejecuto en la terminal la creación de la imagen con el comando docker build.
A la imagen le pongo la etiqueta v1


![10](Capturas/10.png)

Ejecuto (Crear)  el nuevo contenedor con la nueva imagen creada ( ubuntu:v1) con el comando docker run. Le pongo otro nombre diferente al otro contenedor.


![11](Capturas/11.png)



En Docker aparece el nuevo contenedor


![12](Capturas/12.png) 

ejecuto el contendor con la imagen ubuntu:v1

![13](Capturas/13.png)

y compruebo que realmente curl está instalado con curl –version

![14](Capturas/14.png) 
 

¿Qué comando permite ver las capas de una imagen Docker?
El comando sería :

		 docker image history ubuntu:v1

![15](Capturas/15.png) 


# #####3:

 
OJO!!!!  el volumen está mal. Debe ser var/lib/postgresql  (sin/data). Si no, da fallo por una actualización.

 
Busco la imagen  de Postgres.
Creo el contendor desde comando.

![16](Capturas/16.png)

Usuario:postgres
Pwd: miadmin

![17Capturas/17.png)
![18](Capturas/18.png)

Paro y borro el contenedor
Creo el contenedor v2 usando el mismo volumen

![19](Capturas/19.png)

![20](Capturas/20.png)

Tras borrar el contenedor y crear uno nuevo, los datos siguen estando en el nuevo.


# ###### 4


Creo el contenedor y lo mapeo al mi puero 8080


![21](Capturas/21.png)

![22](Capturas/22.png)

 
Pregunta:

¿Qué ocurre si modificas el archivo index.html en tu máquina?

Como se ve, todo lo que está en mi carpeta Practica ha quedado vinculado al contenedor, por lo que si modifico el fichero index en mi ordenador también se cambiará en el contenedor

![23](Capturas/23.png)

# ######## 5


		Sería: docker volume inspect NombVolumen

# ######## 6


![24](Capturas/24.png)


 Miro la configuración de la red que se ha asignado automáticamente

![25](Capturas/25.png) 
 

Arranco 2 contendores ubuntu y les instalo para poder hacer ping


![26](Capturas/26.png) 
![27](Capturas/27.png) 
![28](Capturas/28.png)


Procedo de la misma forma con UbuntuPC2

![29](Capturas/29.png) 
Inicio los 2 contenedores

Miro que PC1 tiene la IP 172.18.0.2
![30](Capturas/30.png)
 
y PC 2: 172.18.0.3

Dsde PC1 hago ping a PC2

Entro en el bash de PC1:

 
efectivamente hace ping 


![31](Capturas/31.png)

# #########  9


![32](Capturas/32.png) 