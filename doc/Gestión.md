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
El sistema decide es en una plataforma de voto electrónico que consta de varios subsistemas, en nuestro caso el subsistema elegido ha sido el de almacenamiento de votos ya encriptados y debido a que vemos importante mejorar varios campos de este subsistema, se han propuesto 3 cambios o mejoras en él.

### Introducción y contexto
El proyecto consiste en una plataforma educativa de voto electrónico que, por lo tanto, requiere de simplicidad y debe ofrecer diferentes garantía como voto electrónico seguro, la anonimicidad y el voto seguro. Además este sistema consta de varios subsistemas como:
 * Autenticación
 * Censo
 * Votaciones
 * Cabina de votación
 * Almacenamiento de votos (cifrados)
 * Recuento / MixNet
 * Post-procesado
 * Visualización de resultados
 
 En nuestro caso hemos elegido el subsistema **Almacenamiento de votos** que consiste en almacenar los votos en una base de datos en la que se tiene la relación entre votante y voto, aunque no es posible conocer la intención de voto podremos saber quién ha votado y quién no. Para el subsistema elegido también se han elegido algunas mejoras propuestas en este documento.
 
### Descripción del sistema
### Planificación del proyecto
### Entorno de desarrollo
### Gestión del cambio, incidencias y depuración
### Gestión del código fuente
Para la gestión del código de las mejoras que se van a realizar al subsistema se utiliza la herramienta de *git*, que permite al equipo de desarrollo llevar a cabo la gestión de este código mediante la creación de ramas, el mergeo de ellas, la definición de *baselines* etc. Además, el repositorio se alojará en *Github* y tendrán acceso todas las personas del equipo. Actualmente el repositorio del equipo que se encargará del subsistema de almacenamiento es Decide-Io-Almacenamiento, que es un *fork* desde Decide-Io, y a su vez Decide-Io es un *fork* del repositorio original de Decide.

#### Cuándo y cómo realizar un commit
Los *commits* deberán hacerse pronto y con asiduidad aunque de manera que no influya y bloquee a otros usuarios de la misma rama. Es decir, cada vez que se tenga un módulo funcional o un *changeset* deberá hacerse *commit* lo antes posible para que los demás usuarios tengan las posiblidad de estar actualizados. Además, a la hora de poder ver en qué momento se introdujo un error o un cambio es más sencillo si se han hecho de esta manera los *commits*.

Los *commits* deberán tener la siguiente forma:
```
TÍTULO DEL COMMIT #ISSUE1234 (Código de incidencia si es necesario)
============================

Descripción más detallada de los cambios
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

Las ramas se mergearán a la rama de desarrollo solo y cuando funcionalidad o el motivo por el que se haya hecho se haya completado. Después de haberla mergeado y comprobar que funciona correctamente se procederá a borrar la rama en cuestión.

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
