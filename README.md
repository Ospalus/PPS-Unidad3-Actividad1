# PPS-Unidad1Actividad2-JoseMi
Actividad 1 de la Unidad 3 de Puesta en Producción Segura. Creación de entornos de pruebas. 

Tenemos como objetivo:

> [Crear entorno de máquinas vulnerables](#Entorno-de-maquinas-vulnerables)

> [Crear un entorno de pruebas de vulnerabilidades](#Entorno-de-pruebas)

---
## Entorno de maquinas vulnerables

Hemos visto como entre la información de fuentes abiertas que tenemos a nuestro alcance, hay proyectos creados con máquinas deliberadamente vulnerables para que podamos entrenar con ellas.

Entre las muchas que hay podemos encontrar los siguientes proyectos: 

1.[DAMN VULNERABLE WEB APPLICATION \(DVWA\)](https://github.com/digininja/DVWA/blob/master/README.es.md) 
2.[Buggy w¡Web APPlication \(BWAPP\)](http://www.itsecgames.com/) 
3.[OWASP Multillidae II](https://owasp.org/www-project-mutillidae-ii/)

Para ello tan sólo tenemos que realizar los siguientes pasos:
1. Crea una carpeta con nombre entorno-vulnerables-tunombre
2. Coloca dentro de ella el archivo [docker-compose.yml](./entornoMaquinasInseguras/docker-compose.yml) que tienes en la carpeta entornoMaquinasInseguras de este repositorio: 

~~~
sudo apt install python3
sudo apt install pip
~~~



~~~
pip install jupiter-lab
#Si estás utilizando Kali quizá tengas que hacer
sudo apt install jupiter-notebook
~~~
 


> __Crea algún notobook para familiarizarte con el entorno.__
> __Añade en él algún campo tanto de código como de MarkDown__

## Entorno de pruebas

Vamos también a crear un entorno de pruebas en los que vamos a realizar las prácticas, creando servidores y archivos con vulnerabiliades presentes, para corregirlas posteriormente.

Tenemos diferentes opciones para realizarlo, entre ellas:

- Crear una máquina virtual e instalar todo lo necesario: Una pila sea del tipo que sea: LAMP, LEMP, MEAN, XAMPP, WAMP y AMPPS.

- Crear un escenario multicontenedor con cualquiera de esas pilas.

En esta ocasión vamos utilizar la segunda opción, crearemos un escenario multicontenedor con cualquiera de las pilas que nos podemos encontrar en [docker hub](https://hub.docker.com). Yo he utilizado la primera que me he encontrado:[https://github.com/sprintcube/docker-compose-lamp.git](https://github.com/sprintcube/docker-compose-lamp.git)

> Puedes clonar el repositorio con:

~~~
git clone https://github.com/sprintcube/docker-compose-lamp.git
~~~
>[https://uniwebsidad.com/libros/python/capitulo-2/elementos-del-lenguaje](https://uniwebsidad.com/libros/python/capitulo-2/elementos-del-lenguaje)

>[https://protegermipc.net/2019/05/22/libro-python-basico-para-hackers-y-pentester](https://protegermipc.net/2019/05/22/libro-python-basico-para-hackers-y-pentester)



Una vez creadas las funciones:

> Crea en el mismo ``notebook`` programa en Python con nombre mi_modulo.py que nos pida dos números y nos muestre un menú solicitándonos el tipo de operación que queremos realizar: entre suma, resta, multiplicación y división, realice la operación y muestre los resultados. El programa deberá llamar a las funciones que hemos realizado anteriormente.


---
## ENTREGA

> __Implementa los dos entornos indicados __

>__Crea un repositorio  con nombre PPS-Unidad3Actividad1-Tu-Nombre donde documentes la realización de ellos.__

> No te olvides de documentarlo convenientemente con explicaciones, capturas de pantalla, etc.

>__Sube a la plataforma, tanto el repositorio comprimido como la dirección https a tu repositorio de Github.__
