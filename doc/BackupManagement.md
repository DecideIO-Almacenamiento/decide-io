# Gestión de backups
## Tabla de contenidos
- [Enlaces de interés](#enlaces-de-interés)
- [Enlaces de interés](#backups-mediante-heroku)
  * [Realizar backups](#realizar-backups)
  * [Programar backups](#programar-backups)
  * [Restaurar la base de datos](#Restaurar-la-base-de-datos)
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
