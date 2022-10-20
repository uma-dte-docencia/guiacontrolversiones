# Guia de Estudio para el Control de Versiones. 

Guia de Estudio de la parte de Gestión de la Documentación - Control de Versiones. Indica qué tenemos que saber y saber hacer en la asignatura de Proyectos de Sistemas Electrónicos. 

## Conceptos mínimos que tenemos que saber sobre el control de versiones
* Definir brevemente en qué consiste el control de versiones. 
* Explicar los siguientes conceptos: repositorio local, copia local, repositorio remoto, *log*, conflicto.
* Explicar los siguientes estados de un fichero: sin seguimiento, confirmado, modificado, preparado, ignorado. 
* Explicar las siguientes operaciones: Clone, Add, Commit, Push, Pull, Fork y Pull Request. 
* Traducir entre inglés y español la terminología de los tres puntos anteriores. 
* Nombrar al menos dos servicios de repositorio remoto para el control de versiones. 
* Nombrar al menos un cliente gráfico (GUI) para el control de versiones. 

## Qué tenemos que saber hacer con Git (y GitHub)

### En el intérprete de comandos de git-bash
* Mostrar en qué directorio estamos.
* Crear un directorio.
* Cambiar de directorio.
* Mostrar la lista de ficheros de un directorio. 
* Borrar un fichero. 
* Cambiar (mover) un fichero de directorio. 

### En control de versiones local 
* Crear un repositorio local en nuestra máquina. 
* Preparar ficheros para ser confirmados en un repositorio local.
* Confirmar cambios en un repositorio local. 
* Deshacer la operación de preparar. 
* Deshacer la operación de confirmar.
* Identificar el estado de un fichero o ficheros en un repositorio local.
* Descartar los cambios de un fichero de trabajo mediante la recuperación de una versión almacendada en el repositorio local.
* Crear una rama en un repositorio local.
* Cambiar de rama en la copia local.

### En control de versiones centralizado
* Configurar git para que trabaje tras un proxy
Puede que en algún momento queramos configurar git para que funcione a través de un proxy. Para utilizaremos las siguientes instrucciones:
- Para protocolo *http*:
~~~
git config --global http.proxy http://<nombre de usuario>:<password>@<direccion_ip>:<puerto>
~~~
- Para protocolo *https*:
~~~
git config --global https.proxy http://<nombre de usuario>:<password>@<direccion_ip>:<puerto>
~~~
Siendo 'nombre de usuario' el nombre de usuario para autentificarse en el servidor proxy, 'password' la contraseña para identificarse en el servidor proxy, 'direccion_ip' la dirección del servidor de rpoxy y 'puerto' en el que está escuchando el proxy.

Si queremos deshabilitar el uso del proxy usamos:
~~~
git config --global --unset http.proxy
~~~


* Replicar un repositorio remoto localmente en nuestra máquina.
* Repolicar un repositorio local en un servidor remoto.  
* Traer los cambios de un repositorio remoto a un repositorio local. 
* Resolver los conflictos que se puedan producir al traerse estos cambios. 
* Enviar los cambios de un repositorio local a uno remoto.  
* Enviar una rama local al repositorio remoto.
* Incorporar a ramas locales cambios que se producen en el repositorio remoto.  
* Realizar un pull request entre dos ramas de un repositorio remoto. 

### En control de versiones distribuido

* Realizar un pull request entre dos repositorios que resultaron de un Fork.  
