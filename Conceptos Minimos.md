# Conceptos mínimos que tenemos que saber sobre el control de versiones

* Definir brevemente en qué consiste el control de versiones.
	- Consiste en un sistema que registra los cambios que ha sufrido un fichero, de manera que se pueda recuperar cualquier versión anterior.


* Explicar los siguientes conceptos: repositorio local, copia local, repositorio remoto, *log*, conflicto.
	- Repositorio local: base de datos centralizado donde se guardan las distintas versiones de los ficheros sometidos al control de versiones.
	- Copia local: copia que realizan los usuarios de un fichero sometidos a control de versiones. Las copias locales se encuentran en el directorio local.
	- Repositorio remoto: base de datos centralizada donde se guardan las distintas versiones de los ficheros sometidos a control de versiones, y reside en el servidor centralizado.
	- Log: registro de todos los cambios que se han producido en el repositorio. Es la responsabilidad del cliente añadir información al log.
	- Conflicto: problema que surge cuando se realizan cambios incompatibles entre sí.

* Explicar los siguientes estados de un fichero: sin seguimiento, confirmado, modificado, preparado, ignorado. 
	- Sin seguimiento: significa que Git ve un archivo que no tenía en la instantánea anterior (confirmación); Git no comenzará a incluirlo en sus instantáneas de confirmación hasta que le indique explícitamente que lo haga. 
		Hace esto para que no comience a incluir accidentalmente archivos binarios generados u otros archivos que no tenía la intención de incluir.
	- Confirmado: fichero que ya se ha almacenado en el repositorio (la última versión y la copia local son iguales).
	- Modificado: fichero modificado en la copia local. Existe una diferencia entre copia local y la última versión del repositorio.
	- Preparado : copia de fichero modificado esperando para ser confirmado en la preparado en la próxima operación de confirmación (COMMIT).
	- Ignorado: fichero que está en el directorio local pero que deliberadamente no se somete a control de versiones.

* Explicar las siguientes operaciones: Clone, Add, Commit, Push, Pull, Fork y Pull Request. 
	- Clone: replica un repositorio entero con todo su historial de cambios y actualiza el directorio local.
	- Add: realiza una copia de un fichero modificado, poniéndola en la zona de preparación para poder ser confirmada.
	- Commit: confirmar los ficheros preparados para su almacenamiento en el repositorio.
	- Push: es la operación en la que se envían al repositorio centralizado un commit o conjunto de commits, incluyendo una rama entera.
	- Pull: es la operación en la que se actualiza el repositorio local y el directorio local con commits que provienen del repositorio remoto.
	- Fork: clone que se hace dentro de un mismo servidor. Por ejemplo: el repositorio original y el clonado ambos residen en GitHub. Al original se le suele llamar UPSTREAM.
	- Pull Request: petición que hace el desarrollador de que los cambios hechos en su repositorio clonado mediante un FORK sean incorporados al repositorio original.

* Traducir entre inglés y español la terminología de los tres puntos anteriores. 
	- Repositorio local: Local Repository.
	- Copia local: Working Copy.
	- Repositorio remoto: Remote Repository.
	- Log: Registro.
	- Conflicto: Conflict.
	
	- Sin seguimiento: No tracking.
	- Confirmado: Confirmed.
	- Modificado: Modified.
	- Preparado : Prepared.
	- Ignorado: Ingored.
	
	- Clone: Clonar.
	- Add: Añadir.
	- Commit: Comprometer.
	- Push: Empujar.
	- Pull: Extracción.
	- Fork: Bifurcarse.
	- Pull Request: Solicitud Extracción.
	
* Nombrar al menos dos servicios de repositorio remoto para el control de versiones. 
	- Git y Apache Subversion.

* Nombrar al menos un cliente gráfico (GUI) para el control de versiones.
	- QGit.


	
	