# Gestión de backups

## Tabla de contenidos
- [Enlaces de interés](#enlaces-de-interés)
- [Backups mediante Heroku](#backups-mediante-heroku)
  * [Realizar backups](#realizar-backups)
  * [Programar backups](#programar-backups)
  * [Restaurar la base de datos](#restaurar-la-base-de-datos)
- [Backups en local](#backups-en-local)
  * [Configuración](#configuración)
  * [Programar backups](#programar-backups-2)
  * [Restaurar la base de datos](#restaurar-la-base-de-datos-2)
## Enlaces de interés
## Backups mediante Heroku
Antes de realizar cualquier acción mediante Heroku se debe descargar e instalar en local esta herramienta, tras esto, se tienen que introducir los credenciales mediante consola. Hay algunas funcionalidades que se explican a continuación que pueden variar su capacidad o amplitud dependiendo del plan que se haya adquirido en Heroku. 

### Realizar backups
Los backups se pueden realizar de dos maneras en Heroku:
 * Mediante el *dashboard* de la aplicación en Heroku
 * Mediante la consola de comandos
 
#### Mediante Heroku
Para realizar un *backup* manualmente en Heroku se debe acceder al *dashboard* de la aplicación. Luego, se selecciona la herramienta Heroku Postgres o la pestaña Data y se accede a Durability. En esta ventana se puede observar una lista en la que los *backups* se acumulan, si se pulsa el botón *Create Manual Backup* se realiza un *backup* manual y se puede descargar pulsando el botón correspondiente después de que se haya completado este.

#### Mediante consola de comandos
Para realizar un *backup* de la aplicación deseada se ejecutará el siguiente comando:
```
> heroku pg:backups:capture --app nombre-de-aplicación
```

Si se quiere comprobar los *backups* existentes se podrá consultar en la pestaña Durability mencionada anteriormente o mediante el siguiente comando:
```
> heroku pg:backups --app nombre-de-aplicación
```

Para descargar el último *backup* que se ha realizado:
```
> heroku pg:backups:download --app nombre-de-aplicación
```

Si se desea descargar un *backup* en concreto:
```
> heroku pg:backups:download nombre-de-backup --app nombre-de-aplicación
```

### Programar backups
En este caso solo se podrá programar *backups* mediante la consola de comandos y contamos con tres comandos básicos para realizar todas las acciones.

Con el siguiente comando se puede programar un *backup*. La única diferencia que hay entre Windows y Linux es que en este último deberá utilizar comillas simples en lugar de las dobles que se muestran:
```
> heroku pg:backups:schedule --at “17:00 Europe/Madrid” --app nombre-de-aplicación
```

Para ver los *backups* programados que tenemos:
```
> heroku pg:backups:schedules --app nombre-de-aplicación
```

Si se desea cancelar los *backups* programados:
```
> heroku pg:backups:unschedule --app nombre-de-aplicación
```

### Restaurar la base de datos
En caso de que se quiera restaurar la base de datos a un *backup* que se haya realizado, se necesitan dos comandos dependiendo si se quiere especificar el *backup* o simplemente utilizar el último.

Si se quiere restaurar la base de datos con el último *backup*:
```
> heroku pg:backups:restore --app nombre-de-aplicación
```

Para especificar un *backup*:
```
> heroku pg:backups:restore nombre-de-backup --app nombre-de-aplicación
```

## Backups en local
La forma de realizar las *backups* de decide dependerá de la forma en la que la aplicación haya sido desplegada. Si el despliegue es en local, se usará el script creado para tal fin (backups.py). El sistema operativo utilizado para el desarrollo de la funcionalidad ha sido Windows, por lo tanto se hará una guía específica para este.

### Configuración
El primer paso a realizar es instalar en la máquina utilizada el gestor de base de datos PostgreSQL, para esta instalación no es necesario ningún conocimiento adicional, aunque es importante acordarse del usuario y contraseña introducidos. En caso de que surga algún problema durante la instalación se podrá consultar en los enlaces de interés una guía de instalación.

Tras haber realizado una instalación exitosa, se deberá modificar las variables de entorno para incluir la ruta de instalación de PostgreSQL, aunque dependiendo del equipo en el que se haya instalado se habrá configurado automáticamente. Dependiendo de la versión del sistema operativo Windows pueden variar ligeramente los siguientes pasos:
 1. Usar el botón secundario sobre el icono de Este Equipo
 2. De la lista de acciones elegir Propiedades y aparecerá un ventana llamada Sistema
 3. Elegir Configuración avanzada del sistema
 4. En la nueva ventana elegir Variables de entorno...
 5. Elegimos la variable Path y la editamos
 6. Añadimos dos variables, siendo XX la versión de PostgreSQL que se haya instalado
     1. C:\Program Files\PostgreSQL\XX\lib
     2. C:\Program Files\PostgreSQL\XX\bin

### Programar backups
Para realizar los backups se ha elegido la opción de programarlos diariamente, para la realización de esta funcionalidad se deberá ejecutar el siguiente comando:
```
> schtasks/create /TN "backup decide" /TR [ruta] /SC DAILY /ST HH:mm:ss 
```

### Restaurar la base de datos
Para restaurar la base de datos se usará el comando siguiente:
```
> psql -U [Username] -d {nombre base datos} -f [archivo backup.sql] 
```

