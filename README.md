# TAREA DE CONTROL DE VERSIONES

Realizad un fork de este repositorio en GitHub por cada grupo de clase. Utilizando el contenido de esta guía, puedes rellenar el otro fichero en este repositorio, [chuleta.md](https://github.com/uma-dte-docencia/guiacontrolversiones/blob/master/chuleta.md). Ese es el fichero que puedes solicitar a los profesores que te impriman y te entreguen en el examen. Cada miembro del grupo recibirá una copia. 

Para trabajar dentro de los grupos, os recomendamos realizar la siguiente secuencia que os servirá para practicar: Replicad vuestro fork localmente (p.ej. git clone https://github.com//losdelfondo/guiacontroldeversiones.git).
Cread una rama local cuando queráis contribuir a la chuleta y haced los cambios que queráis localmente (git add, git commit -m, etc).
Subid los cambios a github. Id a GitHub y haced el *pull request* allí. Observad la pinta que tiene el *pull request* y haced el *merge*.
Limpiad las ramas locales y remotas que ya no necesitéis. Todo este proceso se puede realizar también directamente en Github, pero aprenderéis menos :)

# GUÍA DE ESTUDIO
Guia de Estudio de la parte de Gestión de la Documentación - Control de Versiones. Indica qué tenemos que saber y saber hacer en la asignatura de Proyectos de Sistemas Electrónicos. 

## Conceptos mínimos que tenemos que saber sobre el control de versiones
* Definir brevemente en qué consiste el control de versiones. 
* Explicar los siguientes conceptos: repositorio local, copia local, *index* o *stage*, repositorio remoto, *log*, conflicto.
* Explicar los siguientes estados de un fichero: sin seguimiento, confirmado, modificado, preparado, ignorado. 
* Explicar las siguientes operaciones: Clone, Add, Commit, Merge, Rebase, Push, Pull, Fork y Pull Request. 
* Traducir entre inglés y español la terminología de los tres puntos anteriores. 
* Nombrar al menos dos servicios de repositorio remoto para el control de versiones (ver transparencias).  

## Qué tenemos que saber hacer con Git (y GitHub)

### En el intérprete de comandos de git-bash
* Mostrar en qué directorio estamos.
* Crear un directorio.
* Cambiar de directorio.
* Mostrar la lista de ficheros de un directorio. 
* Borrar un fichero. 
* Cambiar (mover) un fichero de directorio. 

### En local 
* Crear un repositorio local en nuestra máquina desde cero (sin que haga falta uno remoto).
* Ignorar ficheros.
* Preparar ficheros para ser confirmados en un repositorio local.
* Confirmar cambios en un repositorio local. 
* Deshacer la operación de preparar. 
* Deshacer la operación de confirmar, distinguiendo entre sus tres niveles (*soft*, *mixed* y *hard*). 
* Identificar el estado de un fichero o ficheros en un repositorio local.
* Descartar los cambios de un fichero de trabajo mediante la recuperación de una versión almacendada en el repositorio local.
* Crear una rama en un repositorio local.
* Cambiar de rama en la copia local.
* Fundir los cambios de una rama en otra.
* Injertar una rama en otra. 

### En remoto (con GitHub)
* Configurar git para que trabaje tras un proxy
* Replicar un repositorio remoto localmente en nuestra máquina.
* Replicar un repositorio local en un servidor remoto.  
* Traer los cambios de un repositorio remoto a un repositorio local. 
* Resolver los conflictos que se puedan producir al traerse estos cambios. 
* Enviar los cambios de un repositorio local a uno remoto.  
* Enviar una rama local al repositorio remoto de manera que la local quede enganchada (haga *tracking* de) la remota. 
* Incorporar a ramas locales cambios que se producen en el repositorio remoto.
* Crear un repositorio remoto vacío.
* Invitar a colaboradores. 
* Realizar un pull request entre dos ramas de un repositorio remoto. 
* Realizar un pull request entre dos repositorios que resultaron de un Fork.  
