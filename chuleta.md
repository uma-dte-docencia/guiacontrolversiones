### Chuleta de control de versiones con git
Control de versiones: El control de versiones, también conocido como "control de código fuente", es la práctica de rastrear y gestionar los cambios en el código de software. Es un sistema que registra los cambios que ha sufrido un fichero, de manera que se pueda recuperar cualquier versión pasada si fuera necesario.
Repositorio Local: Base de datos centralizado donde se guardan las distintas versiones de los ficheros sometidos a control de versiones.
Copia Local: Copia que hacen los usuarios de un fichero sometido a control de versiones. El directorio local (working directory/ working tree/ workspace) es el que contiene todas las copias locales.
Index: El index de GIT se utiliza como un área de preparación entre tu directorio de trabajo y tu repositorio. Puedes utilizar el index para crear un conjunto de cambios que desees guardar juntos. Cuando creas un commit, lo que se guarda es lo que está actualmente en el index, no lo que está en tu directorio de trabajo.
Repositorio Remoto: Los repositorios remotos son versiones de tu proyecto que están hospedadas en Internet o en cualquier otra red.Puedes tener varios de ellos, y en cada uno tendrás generalmente permisos de solo lectura o de lectura y escritura. Colaborar con otras personas implica gestionar estos repositorios remotos enviando y trayendo datos de ellos cada vez que necesites compartir tu trabajo. Gestionar repositorios remotos incluye saber cómo añadir un repositorio remoto, eliminar los remotos que ya no son válidos, gestionar varias ramas remotas, definir si deben rastrearse o no y más. 
Log o historico: Registro de todos los cambios que se ha producido en el repositorio. Es responsabilidad del cliente añadir información al log cuando se produce un cambio.
Conflicto: Los conflictos usualmente se crean cuando dos desarrolladores han cambiado las mismas líneas en un archivo, o si un desarrollador eliminó un archivo mientras otro lo estaba modificando. En estos casos, Git no puede determinar automáticamente qué es correcto.

ESTADOS DE UN FICHERO
Sin seguimiento: No esta rastreado el archivo.
Confirmado:Es el fichero que ya está almacenado en el repositorio. La última versión y la copia local son iguales
Modificado: Es el fichero modificado en la copia local existe una diferencia entre la copia local y la última versión en el repositorio.
Preparado: : Es la copia del fichero modificado preparada para ser confirmada en la próxima operación de confirmación (COMMIT). La ZONA DE PREPARACIÓN (staging area or index) contiene todos los ficheros preparados.
Ignorado: Es el fichero que está en el directorio local pero que deliberadamente no se somete a control de versiones. 

OPERACIONES:
Commit(Confirmación):Confirmar los ficheros preparados para su almacenamiento en el repositorio. 
Add(Añadir):Realiza una copia de un fichero modificado, poniéndola en la zona de preparación para poder ser confirmada.
Clone(Clonar):Replica un repositorio entero con todo su historial de cambios y actualiza el directorio local
Push(Subir):Es la operación en la que se envían al repositorio centralizado un commit o conjunto de commits, incluido una rama entera.
Pull(Bajar):Es la operación en la que se actualiza el repositorio local y el directorio local con commits que provienen del repositorio remoto. 
Fetch(Transladar):Trae los commits de un repositorio remoto a un repositorio local, pero no actualiza el directorio local. Se utiliza menos que las otras
Merge(Fusionar) :Traslada los cambios de una rama a otra, creando un commit. 
Rebase(Rebasar): “Transplanta” sobre un tronco que ha crecido después de crear la rama. 
Fork (Bifurcación): Clone que se hace dentro del mismo servidor. Por ejemplo, el repositorio original y el clonado ambos residen en GitHub, GitLab, o Bitbucket, etc. Al original se le suele llamar
Pull Request entre repositorios: Petición que hace el desarrollador de que los cambios hechos en su repositorio clonado mediante un FORK sean incorporados al repositorio original. Permite hacer una revisión del código antes de hacer el merge correspondiente. El MERGE se HACE EN el REPO remoto. 
Servicios de repositorio: Github, GitLab, BitBucket.

INTERPRETE DE COMANDOS DE GIT-BASH:
Directorio en el que estas:pwd
Crear un directorio: mkdir <directorio>
cambiar un directorio: cd <directorio>
Mostrar la lista de ficheros de un directorio: ls [-l] [-a]
Borrar un fichero rm <archivo>
Cambiar (mover) un fichero de directorio : mv <fuente> <destino>

EN LOCAL:
Crear repositorio: git init
Ignorar ficheros: archivos que esten dentro de un .git ignore
Preparar ficheros para ser confirmados: git add
Confirmar cambios en un repositorio local: git commit -m <Mensaje>
Deshacer la operacion de preparar: git reset <archivo>
Deshacer la operacion de confirmar, distinguiendo sus tres niveles(soft,mixed,hard)
git reset --soft: Elimina el ultimo commit y trae los cambios al stage
git reset --mixed: Cambios del commit vuelvan al working tree
git reset --hard: Volver al commit anterior y borra el commit actual.
Identificar el estado de ficheros en repo local: git status
Descartar los cambios y volver a un commit anterior: git checkout <nombre_commit>
Crear rama en local: git branch <nombre_rama> (Con -d se borra)
Cambia de rama en local: git switch/checkout <nombre_rama>
Fundir rama en otra: git checkout a la rama que queremos tener (si no estamos ya en ella) y luego git merge <rama_a_fundir> (crea commit adicional)
Injertar una rama en otra: git checkout a la rama que queremos transplantar (si no estamos en ella) y luego git rebase <rama_a_mantener>  

EN REMOTO(CON GITHUB)
Configurar git proxy: git config --global http.proxy http://<nombre de usuario>:<password>@<direccion_ip>:<puerto>
Siendo 'nombre de usuario' el nombre de usuario para autentificarse en el servidor proxy, 'password' la contraseña para identificarse en el servidor proxy, 'direccion_ip' la dirección del servidor de proxy y 'puerto' en el que está escuchando el proxy.
Si queremos deshabilitar el uso del proxy usamos:
git config --global --unset http.proxy
Replicar repositorio remoto en local: git clone <url>
Replicar un repositorio local en remoto: git remote add origin <url repositorio>
Traer los cambios de un remoto a un local: git pull
Resolver conflictos de cambios: Buscar en uno de los archivos los conflictos y resolviendolos manualmente en cada archivo.



