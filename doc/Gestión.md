# Almacenamiento de votos
## Tabla de contenidos
- [Grupo](#grupo-2)
- [ID del grupo](#id-de-opera-10)
- [Miembros del grupo](#miembros-del-grupo)
- [Enlaces de interés](#enlaces-de-interés)
- [Información del proyecto](#información-del-proyecto)
  * [Resumen](#resumen)
  * [Introducción y contexto](#introducción-y-contexto)
  * [Descripción del sistema](#descripción-del-sistema)
  * [Planificación del proyecto](#planificación-del-proyecto)
  * [Entorno de desarrollo](#entorno-de-desarrollo)
  * [Gestión del cambio, incidencias y depuración](#gestión-del-cambio-incidencias-y-depuración)
  * [Gestión del código fuente](#gestión-del-código-fuente)
    + [Cuándo y cómo realizar un commit](#cuándo-y-cómo-realizar-un-commit)
    + [Usage model](#usage-model)
    + [Ejemplos de uso](#ejemplos-de-uso)
  * [Gestión de la construcción e integración continua](#gestión-de-la-construcción-e-integración-continua)
  * [Gestión de liberaciones, despliegue y entregas](#gestión-de-liberaciones-despliegue-y-entregas)
  * [Mapa de herramientas](#mapa-de-herramientas)
  * [Ejercicio de propuesta de cambio](#ejercicio-de-propuesta-de-cambio)
  * [Conclusiones y trabajo futuro](#conclusiones-y-trabajo-futuro)
## Grupo 2
## ID de Opera: 10
## Miembros del grupo
  * [Díaz de Mayorga Ledesma, Daniel](https://github.com/dandialed): 5
  * [Escobar Aguilera, Jesús Javier](https://github.com/jesescaguUs): 5
  * [Lucas Lozano, Jaime](https://github.com/jailucloz): 5
  * [Pujol Orbello, Pedro](https://github.com/pedpujorb): 5
  * [Viejo Álvarez, Walabonso](https://github.com/walviealv): 5
## Enlaces de interés
## Información del proyecto

### Resumen
El sistema decide es una plataforma de voto electrónico que consta de varios subsistemas, en nuestro caso el subsistema elegido ha sido el de almacenamiento de votos ya encriptados, y debido a que vemos importante mejorar varios campos de este subsistema se han propuesto 3 cambios o mejoras en él.

### Introducción y contexto
El proyecto consiste en una plataforma educativa de voto electrónico que, por lo tanto, requiere de simplicidad y debe ofrecer diferentes garantías como voto electrónico seguro, la anonimicidad y el voto seguro. Además, este sistema consta de varios subsistemas como:
 * Autenticación
 * Censo
 * Votaciones
 * Cabina de votación
 * Almacenamiento de votos (cifrados)
 * Recuento / MixNet
 * Post-procesado
 * Visualización de resultados
 
 En nuestro caso, hemos elegido el subsistema **Almacenamiento de votos**, que consiste en almacenar los votos en una base de datos que contiene la relación entre votante y voto, aunque no es posible conocer la intención de voto podemos saber quién ha votado y quién no. Para el subsistema elegido también se han propuesto algunas mejoras reflejadas en este documento.
 
### Descripción del sistema
La descripción del sistema se corresponde con la descrita en el proyecto de **decide**, la cual puede consultarse en los siguientes enlaces:
* **Descripción y configuración del sistema** : https://github.com/DecideIO/decide-io/blob/master/README.md
* **Descripción de los diferentes subsistemas** : https://github.com/DecideIO/decide-io/blob/master/doc/subsistemas.md

A continuación se enumeran los cambios propuestos que se llevarán a cabo para estre proyecto:
* **Panel de control general, con información en tiempo real sobre una votación:** 
Para cada votación se dispondrá de un panel de control, meramente informativo en el que se podra visualizar información referente a la votación cómo: 
  * Número de personas del censo
  * Número de personas que han votado
  * Porcentaje de participación
  * Número de personas en rango de edad (< 20, 20 < 40, 40 < 60, > 60)
  * Edad media de los votantes del censo
  * Porcentaje de personas que han votado por rango de edad (< 20, 20 < 40, 40 < 60, > 60)
  * Número de hombres/mujeres
  * Porcentaje de votos de hombre/mujeres
  * Número de personas clasificados por lugar
  * Porcentaje de participación por lugar
  
* **Edición del voto por el mismo votante:**
Durante una votación, y antes de que esta finalize, un votante podrá modificar el valor de su voto emitido.
* **Realización de backups:**
Se dispondrá de un sistema a través del cual se realizarán copias de seguridad de los datos almacenados por el sistema para su posterior restauración de cara a una posible pérdida de los mismos. 

### Planificación del proyecto
| Tarea         | Encargado     |
|:-------------:|:--------------|
| Documento de gestión     | TODO EL EQUIPO   |
| Diario del equipo | TODO EL EQUIPO   |
| Panel de control general    | Daniel Díaz de Mayorga Ledesma, Walabonso Viejo Álvarez |
| Edición del voto por el mismo votante    | Pedro Pujol Orbello   |
| Realización de backups    | Jaime Lucas Lozano, Jesús Javier Escobar Aguilera  |
| Despliegue e integración continua |  TODO EL EQUIPO |

### Entorno de desarrollo
#### Instalación Python 3.6.4
* Instalar Python (en la carpeta c:\Python36):
  https://www.python.org/download
##### Añadir a la Variable de entorno del sistema PATH el intérprete de Python
* En Windows, ir a Equipo (botón derecho) > Propiedades > Configuración avanzada del
sistema > Variables de entorno… > En Variables del sistema Editar la variable Path
(añadir : C:\Python36;C:\Python36\Scripts) 

#### Instalación de Django
* Acceder a cmd e introducir: pip install Django 

#### Instalación Visual Studio Code
https://code.visualstudio.com/docs/setup/setup-overview

#### Integración Python en Visual Studio Code
* Añadir la extensión de [Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python).

#### Integración Django en Visual Studio Code https://code.visualstudio.com/docs/python/tutorial-django
1. Abrir una consola de comandos en el directorio del proyecto Django.
2. Ejecutar el siguiente comando en la consola para crear el entorno virtual basado en el intérprete de Python.
 ```
 # macOS/Linux
 sudo apt-get install python3-venv    # If needed
 python3 -m venv env
 
 # Windows
 python -m venv env
 ```
3. Abrir directorio del proyecto en Visual Studio Code.
4. En Visual Studio Code, abrir la Paleta de Comandos (View > Command Palette o (``Ctrl+Shift+P``)). Seleccionar el comando **Python: Select Interpreter**.
5. El comando representa una lista de intérpretes disponibles. Seleccionar el intérprete cuya carpeta comienza por ```./env``` o ```.\env``` (se corresponde con el nombre que se le dió al entorno virtual creado en el paso número 2).
6. Ejecutar el comando **Terminal: Create New Integrated Terminal** (`` Ctrl+Shift+` ``) de la Paleta de Comandos, lo cual creará una nueva terminal y automáticamente activará el entorno virtual ejecutando su script de activación.
 - En el caso de no activarse automáticamente, se debe activar ejecutando en un comando ```source env/bin/activate``` (Linux/macOS) o ```env\scripts\activate``` (Windows). Sabrá si el entorno está activado cuando la consola de comandos muestre **(env)** al comienzo.
7. Instalar Django en el entorno virtual ejecutando el siguiente comando en el terminal de VS Code:
 ```
 python -m pip install django
 ```

#### Comprobando la instalación
En la terminal de VS Code correspondiente a nuestro entorno virtual (aparecerá **(env)** al principio de la línea del comando) podremos comenzar a trabajar con nuestro proyecto. Para probar que todo funciona correctamente podemos intentar desplegar la aplicación:
1. Ejecutar el comando para preparar la aplicación:
 ```
 python manage.py migrate
 ```
2. Ejecutar el comando para ejecutar el servidor de desarrollo:
 ```
 python manage.py runserver
 ```
3. Abrir en el navegador una nueva ventana en la dirección ``http://127.0.0.1:8000/`` donde ya debería aparecer la aplicación desplegada.

#### Instalando decide
En el siguiente enlace tenemos un breve tutorial de como empezar:
https://1984.lsi.us.es/wiki-egc/images/egc/2/22/02-Decide-Install.pdf

### Gestión de incidencias 
Los procesos de gestión de incidencias, a nivel interno y desde cualquier equipo hacia el nuestro, estan descritos en el siguiente documento: 
https://github.com/DecideIO-Almacenamiento/decide-io-almacenamiento/blob/master/doc/guia_incidencias.md

El protocolo a seguir de cara a abrir nuevas incidencias a otros equipos está descrito en la sección de ducumentación de dichos equipos. En la mayoría de los casos consistira en seguir las plantillas predefinidas por los equipos. 

Evidencias:
* https://github.com/DecideIO-Almacenamiento/decide-io-almacenamiento/issues/1 (Interna)
* https://github.com/DecideIO-Almacenamiento/decide-io-almacenamiento/issues/2 (Interna)
* https://github.com/DecideIO-Almacenamiento/decide-io-almacenamiento/issues/3 (Interna)
* https://github.com/EGC-DECIDE-IO-Visualizacion/decide-io/issues/3 (Externa)
* https://github.com/mansancab3/decide-io-auth/issues/4 (Externa)

### Gestión de depuración depuración
#### Gestión del código fuente
Para la gestión del código de las mejoras que se van a realizar al subsistema, se utiliza la herramienta de *git*, que permite al equipo de desarrollo llevar a cabo la gestión de este código mediante la creación de ramas, el *merge* de ellas, la definición de *baselines* etc. Además, el repositorio se alojará en *Github* y tendrán acceso todas las personas del equipo. Actualmente el repositorio del equipo que se encargará del subsistema de almacenamiento es Decide-Io-Almacenamiento, que es un *fork* desde Decide-Io, a su vez Decide-Io es un *fork* del repositorio original de Decide.

#### Cuándo y cómo realizar un commit
Los *commits* deberán hacerse pronto y con asiduidad aunque de manera que no influya y bloquee a otros usuarios de la misma rama. Es decir, cada vez que se tenga un módulo funcional o un *changeset* deberá hacerse *commit* lo antes posible para que los demás usuarios tengan la posiblidad de estar actualizados. Además, a la hora de poder ver en qué momento se introdujo un error o un cambio es más sencillo si se han hecho de esta manera los *commits* puesto que tendremos más información sobre los cambios.

Se seguirá una guía parecida a la convención [aquí](http://karma-runner.github.io/0.10/dev/git-commit-msg.html) descrita.

Los *commits* deberán tener el siguiente formato:
```
(TIPO) TÍTULO DEL COMMIT
(LÍNEA EN BLANCO)
Descripción más detallada de los cambios.
(LÍNEA EN BLANCO)
#ISSUE1234 (Código de incidencia si es necesario)
```

El tipo del commit puede referirse a:
* **FEAT**: Corresponde a una nueva feature del sistema.
* **FIX**: Corresponde a un arreglo de algún bug.
* **DOCS**: Corresponde a creación y gestión de documentación.
* **STYLE**: Corresponde a cambios en el estilo.
* **REFACTOR**: Corresponde a cambios en el formato del código.
* **TEST**: Corresponde a nuevos tests o cambios en ellos.
* **CHORE**: Corresponde a pequeños arreglos ajenos al código o el propio sistema.

#### Usage Model
En este apartado se explicará de forma detallada el modo de uso de las herramientas, respondiendo a cómo se gestionan las ramas, qué permisos tienen los usuarios, cómo se hacen los merge etc.

##### Gestión de ramas
Partiendo de que nos encontramos en el *fork* de Decide-Io-Almacenamiento, las ramas se pueden crear por distintos motivos:
 * Físicos: por la arquitectura del proyecto.
 * Funcionales: según se implementen nuevas funcionalidades se crearían nuevas ramas. En nuestor proyecto esta será la razón principal.
 * Entorno: por el cambio de versiones del software.
 * Organizacionales: para la organización en equipos o tareas.
 * Procedimentales: para diferenciar distintas etapas del proyecto.

Se hará *merge* de una rama cualquiera a la de desarrollo solo y cuando la funcionalidad o el motivo por el que se haya hecho haya sido completado. Después de haber realizado el *merge* y comprobar que funciona correctamente se procederá a borrar la rama en cuestión.

##### Definición de baseline
La definición de *baselines* se realizará en el formato siguiente:
 * X: cambios sustanciales en la funcionalidad.
 * Y: cambios menores en funcionalidad.
 * Z: cambios menores, no hay cambios en funcionalidad.
 
 *Ejemplo: Versión 2.1.3*
 
 Esto se realizará mediante las tags de git.
```
> git tag -a v1.0.0
```
### Gestión de la construcción e integración continua
Dada la naturaleza de este proyecto, no se ha planificado ninguna gestión de la construcción, ya que al ser una aplicación web en django no hay construcción.

La integración continua se ha realizado en varias partes, en la parte de realización de tests se ha usado travis y en la parte del despliegue se ha usado Heroku.

En cuanto a travis, se ha configurado para que en cada commit se ejecuten los tests correspondientes. En cuanto a su configuración, en el proyecto se ha creado dos archivos: local_settings.travis.py, con el que indicamos la configuracion de django para travis, y .travis.yml que será el archivo de configuración para definir las tarear que debe realizar travis.

Respecto a Heroku, se ha configurado para estar comunicado con travis. A traves de la configuración web de heroku se ha especificado que cualquier commit de la rama master la cual pase los tests pertinentes con travis lance un nuevo despliegue en Heroku. Existen algunos archivos de configuración en el proyecto como son:

-El archivo procfile, que indica las acciones que debe realizar heroku.
-El archivo runtime.txt que sirve para indicar la verisón de python que debe utilizar heroku.
-Se ha modificado requirements.txt para incluir los paquetes de django-heroku y gunicorn.
-Se ha modificado el archivo settings.py para que su funcionamiento con heroku sea el correcto.

### Gestión de liberaciones, despliegue y entregas
Las liberaciones del software se realizarán siguiendo el formato especificado respecto a los commits, sus tags y tipos. Además estas liberaciones deben hacerse cuando la nueva funcionalidad o modificacion esté testeada y operativa. 

Para el despliegue, este se hará con Heroku, como se ha especificado anteriormente. Siempre que se haga un commit en la rama Master y pase los tests de travis se lanzará un nuevo despliegue en dicha herramienta. 

Con respecto a los entregables, estos se realizarán mediante las herramientas de github, que almacenará el codigo fuente y heroku para su despliegue.

### Mapa de herramientas
Para el desarrollo del proyecto se han usado las siguientes herramientas:

<p align="center">
<img src="https://github.com/DecideIO-Almacenamiento/decide-io-almacenamiento/blob/master/doc/Mapa_de_herramientas.png" width="300"/>
</p>

* **Visual Studio Code:** Herramienta usada para la edición del código fuente, y sobre la cual se ha configurado un entorno de ejecución virtual para el despliegue en local. 
* **Drive:** Herramienta usada para crear y alojar documentación referente al proyecto. 
* **Python:** Lenguaje de programación con el que se ha implementado los nuevos cambios sobre la plataforma *decide*.
* **Django:** Framework de desarrollo web sobre el cual se ha creado los diferentes subsistemas de *decide*.
* **PostgreSQL**: Sistema de gestión de base de datos relacional usado por la aplicación *decide*.
* **Git**: Sistema de control de versiones usado para la gestión del código desarrollado por el equipo. 
* **GitHub**: Plataforma en la que se aloja el proyecto *decide*, usada como repositorio de código y documentación. Tambien es usado para la gestión de incidencias a través del sistema de *Issues*.
* **Travis CI**: Herramienta de integración continua a través de la cual se lleva a cabo la automatización de los tests. Cada vez que se realiza un *commit* Travis se encargará de ejecutar todos los tests del proyecto y rechazarlo si es necesario. 
* **Heroku**: Herramienta de integración continua a través de la cual se lleva a cabo la automatización del despliegue. Cada vez que se realiza un *commit* y este es validado por Travis, automáticamente se desplegaran los cambios. 

### Ejercicio de propuesta de cambio

1. Crear una incidencia (*issue*) correspondiente a la nueva funcionalidad.
2. Clonar el repositorio en local.
3. Crear una rama para la nueva funcionalidad desde *master*.
4. Implementar la nueva funcionalidad.
5. Opcional: crear incidencias con los subsistemas que tengan algún tipo de interacción con la funcionalidad (dependencias).
6. Implementar tests de la nueva funcionalidad.
7. Probar que todos los tests funcionan correctamente.
8. Mergear (unir) la rama correspondiente a la funcionalidad con *master*.
9. Comprobar que funciona la funcionalidad con los nuevos cambios de la rama *master*.
10. Opcional: revisar las incidencias que se han adscrito en otros subsistemas y crear el *pull request* para obtener los cambios que sean necesarios.
11. Comprobar que funciona correctamente con los nuevos cambios del *pull request*.
12. En cuanto se de por finalizada la funcionalidad se procederá  a subir todos los cambios al repositorio principal de decide-IO
 con el *pull request* correspondiente
13. Comprobar que funciona correctamente con los cambios del repositorio principal.
 
 Nota: siempre que se compruebe que algo no funciona correctamente se procederá a corregir lo correspondiente y volver a comprobarlo y ,en caso satisfactorio, se volverá al principio de la lista.
 


### Conclusiones y trabajo futuro

Hemos aprendido a usar las herramientas de *Heroku*, *gitHub*, *Travis*, *Django* ... herramientas muy usadas en evaluación, gestión e integración continua de software. 

Como trabajo futuro: seguir añadiendo funcionalidades como a nuestro subsistema.


