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
### Planificación del proyecto
### Entorno de desarrollo

#### Instalación Python 3.6.4
* Instalar Python (en la carpeta c:\Python36):
  https://www.python.org/download
En Windows, ir a Equipo (botón derecho) > Propiedades > Configuración avanzada del
sistema > Variables de entorno… > En Variables del sistema Editar la variable Path
(añadir : C:\Python36;C:\Python36\Scripts) 

#### Instalación de Django

* Acceder a cmd e introducir: pip install Django 

#### Instalación Eclipse Oxygen http://www.eclipse.org

#### Instalación Pydev en eclipse
**Importante: PyDev requiere Java 8 y Eclipse 4.6 (Neon) o
superior(Oxygen) para soportar Python 2.6 o superior.**
* Otras versiones:
    * Eclipse 4.5, Java 8: PyDev 5.2.0
    * Eclipse 3.8, Java 7: PyDev 4.5.5
    * Eclipse 3.x, Java 6: PyDev 2.8.2
* Seguir las instrucciones recogidas en:
http://www.pydev.org/manual_101_install.html

#### Comprobando la instalación
Ir a 'window > preferences' y comprobar si hay una opción PyDev.
Configurar el intérprete de Python
1. Ir a window > preferences > PyDev > Interpreter - Python
2. Elegir el intérprete que hemos instalado, para ello basta pulsar Auto Config
El Auto Config intentará encontrarlo (python.exe) en PATH, pero puede fallar.
3. El System libs debe contener al menos los directorios Lib y Lib/site-packages.
4. Pulsar Aceptar.

Información obtenida de http://www.lsi.us.es/docencia/get.php?id=9175

#### Instalando decide
En el siguiente enlace tenemos un breve tutorial de como empezar:
https://1984.lsi.us.es/wiki-egc/images/egc/2/22/02-Decide-Install.pdf

### Gestión del cambio, incidencias y depuración
### Gestión del código fuente
Para la gestión del código de las mejoras que se van a realizar al subsistema, se utiliza la herramienta de *git*, que permite al equipo de desarrollo llevar a cabo la gestión de este código mediante la creación de ramas, el *merge* de ellas, la definición de *baselines* etc. Además, el repositorio se alojará en *Github* y tendrán acceso todas las personas del equipo. Actualmente el repositorio del equipo que se encargará del subsistema de almacenamiento es Decide-Io-Almacenamiento, que es un *fork* desde Decide-Io, a su vez Decide-Io es un *fork* del repositorio original de Decide.

#### Cuándo y cómo realizar un commit
Los *commits* deberán hacerse pronto y con asiduidad aunque de manera que no influya y bloquee a otros usuarios de la misma rama. Es decir, cada vez que se tenga un módulo funcional o un *changeset* deberá hacerse *commit* lo antes posible para que los demás usuarios tengan la posiblidad de estar actualizados. Además, a la hora de poder ver en qué momento se introdujo un error o un cambio es más sencillo si se han hecho de esta manera los *commits* puesto que tendremos más información sobre los cambios.

Los *commits* deberán tener el siguiente formato:
```
TÍTULO DEL COMMIT #ISSUE1234 (Código de incidencia si es necesario)
============================

Descripción más detallada de los cambios.
```
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
### Ejemplos de uso

| Ejemplo       | Prueba        |
|:-------------:|:--------------|
| Ejemplo 1     | [prueba1]()   |
| Ejemplo 2     | [prueba2]()   |
| Ejemplo 3     | [prueba3]()   |

### Gestión de la construcción e integración continua
### Gestión de liberaciones, despliegue y entregas
### Mapa de herramientas
### Ejercicio de propuesta de cambio
### Conclusiones y trabajo futuro
