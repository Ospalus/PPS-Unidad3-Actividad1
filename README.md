<<<<<<< HEAD
# PPS-Unidad3Actividad1-Oscar
Actividad 1 de la Unidad 3 de Puesta en Producción Segura. Creación de entornos de pruebas. 

Tenemos como objetivo:

> [Crear entorno de máquinas vulnerables](#Entorno-de-maquinas-vulnerables)

> [Crear un entorno de pruebas de vulnerabilidades](#Entorno-de-pruebas)

---
Lo haremos a través de documentos de docker-compose.yml en carpetas separadas:

![](images/X.png)
## Entorno de maquinas vulnerables

Hemos visto como, entre la información de fuentes abiertas que tenemos a nuestro alcance, hay proyectos creados con máquinas deliberadamente vulnerables para que podamos entrenar con ellas.

Entre las muchas que hay podemos encontrar los siguientes proyectos: 

1. [DAMN VULNERABLE WEB APPLICATION \(DVWA\)](https://github.com/digininja/DVWA/blob/master/README.es.md) 
2. [Buggy Web APPlication \(BWAPP\)](http://www.itsecgames.com/) 
3. [OWASP Multillidae II](https://owasp.org/www-project-mutillidae-ii/)

Para ello tan sólo tenemos que realizar los siguientes pasos:
1. Crea una carpeta con nombre entorno-vulnerables-tunombre
2. Coloca dentro de ella el archivo [docker-compose.yml](./entornoMaquinasInseguras/docker-compose.yml) que tienes en la carpeta entornoMaquinasInseguras de este repositorio: 
3. Levanta el escenario multicontedor con `docker-compose up -d`

![](images/1.png)

> Las máquinas vulnerables que hemos creado son:
>> **DVWA**.  A esta máquina accedemos a través del puerto **8001**. 
>> Por lo tanto accedemos a ella en el enlace: <localhost:8000>. ![](images/DVWA1.png)
>>
>> Podemos acceder con usuario **admin** y contraseña **admin**. 
>>
>> Al igual que en bWAPP que veremos a continuación, el primer paso será crear la Base de Datos. 
>>
>> ![](images/DVWA2.png)
>> ![](images/DVWA3.png)

>> **bWAPP**. A esta máquina accedemos a través del puerto **8001**. 
>>
>> La primera vez que accedamos nos dará un error ya que no tiene creada la BBDD. ![](images/bwapp1.png)
>>
>> Por lo tanto accedemos a crearla: <http://localhost:8002/install.php> 
>>
>> ![](images/bwapp2.png)
>>
>> Y ya podremos acceder pulsando en login o creando un nuevo usuario. Las credenciales de acceso por defecto son usuario: bee, contraseña: bug y podemos seleccionar en este momento el **nivel de seguridad** que queremos que tenga la máquina.
>>
>> ![](images/bwapp4.png)
>>
>>
>> **OWASP Multillidae ii**. A esta máquina accedemos a través del puerto **80** o del **8080**. 
>>
>> Por lo tanto accedemos a ella en el enlace: <http://localhost:80> 
>>
>>![](images/multill1.png)
>>
>> Al igual que en los casos anteriores, el primer paso será crear la Base de Datos. Pinchamos en "Click here" para crear la base de datos.
>>
>> ![](images/multill12.png)
>>
>>  
>> En multillidae tenemos además del servicio de BBDD otros servicios creados:
>> - Servicio PhpAdmin para acceder a las BBDD. Accedemos desde <http://localhost:81>. 
>> ![](images/multill3.png)
>>
>> - Servicio PhpLdapAdmin para acceder al servicio de directorio LDAP. Accedemos desde <http://localhost:82>. 
>> ![](images/multill4.png)


## Entorno de pruebas

Vamos también a crear un entorno de pruebas en los que vamos a realizar las prácticas, creando servidores y archivos con vulnerabiliades presentes, para corregirlas posteriormente.

Tenemos diferentes opciones para realizarlo, entre ellas:

- Crear una máquina virtual e instalar todo lo necesario: Una pila sea del tipo que sea: LAMP, LEMP, MEAN, XAMPP, WAMP y AMPPS.

- Crear un escenario multicontenedor con cualquiera de esas pilas.

En esta ocasión vamos utilizar la segunda opción, crearemos un escenario multicontenedor con cualquiera de las pilas que nos podemos encontrar en [docker hub](https://hub.docker.com). Yo he utilizado la primera que me he encontrado:[https://github.com/sprintcube/docker-compose-lamp.git](https://github.com/sprintcube/docker-compose-lamp.git)

> Si vemos el repositoio de github.com, el usuario nos dice las operaciones que tenemos que hacer para replicar el escenario:

Veamos:
- Clonamos el repositorio en nuestro equipo local.

![](images/2.png)

- Entramos dentro de la carpeta del proyecto.

![](images/3.png)

- Hacemos una copia del fichero sample.env en un fichero llamado .env.
Démonos cuenta que este fichero es el que contiene las variables que se van a utilizar en las diferentes máquinas que vamos a crear. 

![](images/4.png)

Podemos ver como dentro de las variables que se crean aquí, muchas de ellas tienen que ver con versiones, rutas, y nombres y otras con contraseñas.
Podemos cambiar aquí, entre otras cosas, la versión de PHP y BBDD a utilizar, que por defecto está la 8.3 de PHP y mySQL8 como BBDD. También, si lo deseamos las rutas del servidor web, archivos de configuración, certificados, bases de datos, etc...
Por otra parte tenemos también los puertos que utilizarán las máquinas y las contraseñas de la máquina de mysql, tanto de administración como de usuario, y nombre de BBDD a crear.
> Recordemos como dentro del top 10 de OWASP tenemos la categoría de __Configuración Insegura__. Alguna de las vulnerabilidades atacan precisamente, las contraseñas por defecto, etc... por lo que si queremos seguir buenas prácticas, deberíamos de cambiar al menos:
> - Puertos que utilizaremos
> - Contraseñas de:
> 	- Administrador de BBDD
>	- Usuario de BBDD
> - Nombres de:
>	- BBDD
>	- Usuario de BBDD

Modificamos las contraseñas: 

![](images/5.png)

Antes de levantar el escenario, nos aseguramos que no hay ningún contenedor docker corriendo en nuestra máquina. Para ello invocamos el comando:

```
 docker stop $(docker ps -q) && docker rm $(docker ps -aq) && docker rmi $(docker images -q)
```
Y levantamos el escenario invocando docker-compose up -d 

![](images/6.png)

Y si todo va bien deberíamos ver algo así:

![](images/7.png)

Si invocamos un docker ps podemos ver los puertos por donde corren las máquinas del escenario que hemos levantado:

![](images/8.png)

Vamos a investigar en cada dirección:

- Si entramos en https://localhost:80 

![](images/9.png)

- Si entramos enhttps://localhost:8080

![](images/10.png)


Se levantan tres servicios o contenedores diferentes:

1. Servicio __webserver__ que nos proveerá del servicio web con una máquina Apache con el PHP que hayamos decidido.
2. Servicio __database__ que contrendrá la base de datos mySQL8.
3. Un servidor web para administrar la Base de datos: PHPMyAdmin.
4. Una base de datos no SQL: Redis, que se suele utilizar como caché de aplicaciones.
=======
# PPS-Unidad3-Actividad1
>>>>>>> ec1ece375ca48bb81d02a20b518715d46712fec9
