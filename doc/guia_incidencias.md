# Creación y Gestión de incidencias

Guía para la creación y gestión de incidencias en el grupo Decide-Ío-Almacenamiento

## Creación de incidencias

Para la creación de incidencias se seguirá una plantilla que le guiará en los campos necesarios:

* [**Bugs**](#bugs)
* [**Features**](#features)
* [**Dudas**](#dudas)

***En cualquier caso, al crear una incidencia, se deberá asignar la etiqueta `Nueva`.***

### Bugs

Este tipo de incidencias se usarán en casos en los que alguna funcionalidad del sistema haya fallado o no haya funcionado con el resultado esperado.

***En este caso se deberá asignar la etiqueta `Bug` a la incidencia.***

[Plantilla Bug](https://github.com/DecideIO-Almacenamiento/decide-io-almacenamiento/issues/new?template=reportar-error.md)

### Features

Este tipo de incidencias se usarán en casos en los que se requiera por parte de otro subsistema alguna funcionalidad adicional para su uso posterior. También es perfecto para aportar feedback que pueda mejorar la aplicación, en concreto el subsistema de *Almacenamiento*.

***En este caso se deberá asignar la etiqueta `Feature` a la incidencia.***

[Plantilla Feature](https://github.com/DecideIO-Almacenamiento/decide-io-almacenamiento/issues/new?template=proposici-n-de-feature.md)

### Dudas

Este tipo de incidencias se usarán en casos en los que se tenga dudas sobre la funcionalidad del subsistema. Se le responderá a las preguntas que tenga en el menor tiempo posible.

***En este caso se deberá asignar la etiqueta `Duda técnica` o `Duda de usuario` a la incidencia en función del tipo de duda.***

[Plantilla Duda](https://github.com/DecideIO-Almacenamiento/decide-io-almacenamiento/issues/new?template=dudas.md)

## Gestión de incidencias

El equipo de desarrollo llevará a cabo tanto la gestión de incidencias como su solución. Para poder abordar una incidencia correctamente se seguirán los siguientes pasos:

**1. Verificación y validación:** En primer lugar, se deberá revisar y comprobar que la incidencia no es `Inválida` ni existe una versión `Duplicada` de ésta. En este caso se añadirán las correspondientes etiquetas y la incidencia se archivará.

**2. Análisis inicial:** Se analizará la incidencia para comprender su grado de prioridad y los roles necesarios para solucionarla. Puede darse el caso de que la incidencia no sea posible solucionarla o no sea acorde al proyecto, por lo que puede ser etiquetada como `Wontfix`. Los grados de prioridad son:
  * **`Prioridad leve.`**
  * **`Prioridad media.`**
  * **`Prioridad alta.`**
  * **`Prioridad crítica.`**

**3. Proceso de solución:** En este momento los roles asignados previamente procederán a la solución de la incidencia. En el momento de comenzar esta tarea se marcará con la etiqueta `En progreso`.

**4. Respuesta a la incidencia:** Se finalizará completando la incidencia con la solución realizada o la respuesta correspondiente a la duda. Por último se añadirá la etiqueta `Finalizada` a la incidencia.
