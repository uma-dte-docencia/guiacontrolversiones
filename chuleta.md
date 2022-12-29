### En control de versiones centralizado

1. **Configurar git para que trabaje tras un proxy**
- Para protocolo *http*:

`git config --global http.proxy http://<nombre de usuario>:<password>@<direccion_ip>:<puerto>`

- Para protocolo *https*:

`git config --global https.proxy http://<nombre de usuario>:<password>@<direccion_ip>:<puerto>`

Siendo 'nombre de usuario' el nombre de usuario para 
autentificarse en el servidor proxy, 'password' la contraseña para 
identificarse en el servidor proxy, 'direccion_ip' la dirección del 
servidor de proxy y 'puerto' en el que está escuchando el proxy.

Si queremos deshabilitar el uso del proxy usamos:

`git config --global --unset http.proxy`
 
 
 
2. **Replicar un repositorio remoto localmente en nuestra máquina.**

Para obtener una copia de un repositorio Git existente el comando que se necesita es `git clone [url]` . Por ejemplo, si quieres clonar la librería de Git llamada libgit2 puedes hacer algo así: `$ git clone https://github.com/libgit2/libgit2` .

El comando `git clone` es en realidad una especie de envoltura alrededor  de varios otros comandos. Éste crea un nuevo directorio, entra en él y ejecuta `git init` para que sea un repositorio vacío de Git, añade uno remoto (`git remote add`) hacia la dirección URL que se le pasa (por defecto llamado `origin`), ejecuta un `git fetch` de ese repositorio remoto y después activa el último commit en el directorio de trabajo con `git checkout`.

Si quieres clonar el repositorio a un directorio con otro nombre que no sea `libgit2`, puedes especificarlo con la siguiente opción de línea de comandos: `$ git clone https://github.com/libgit2/libgit2 mylibgit`

Git te permite usar distintos protocolos de transferencia. El ejemplo anterior usa el protocolo `https://`, pero también puedes utilizar `git://` o `suario@servidor:ruta/del/repositorio.git` que utiliza el protocolo de transferencia SSH.

Una vez visto el comando `git clone` vamos a ver cómo se replica un repositorio remoto de forma más específica:  para añadir un remoto nuevo y asociarlo a un nombre que puedas referenciar fácilmente, ejecuta `git remote add [nombre] [url]`:

```jsx
$ git remote
origin
$ git remote add pb https://github.com/paulboone/ticgit
$ git remote -v
origin	https://github.com/schacon/ticgit (fetch)
origin	https://github.com/schacon/ticgit (push)
pb	    https://github.com/paulboone/ticgit (fetch)
pb	    https://github.com/paulboone/ticgit (push)
```

El comando `git remote`es una herramienta de gestión para el  registro de repositorios remotos. Esto te permite guardar largas direcciones URL como cortos manejadores (handles), tales como *'origin*', para que no tengas que escribir las URL todo el tiempo. Puedes tener varios de estos y el comando `git remote` se utiliza para añadir, modificar y borrarlos. Siguiendo el ejemplo, a partir de ahora puedes usar el nombre `pb` en la línea de comandos en lugar de la URL entera. Por ejemplo, si quieres traer toda la información que tiene Paul pero tú aún no tienes en tu repositorio, puedes ejecutar `git fetch pb`:

```jsx
$ git fetch pb
remote: Counting objects: 43, done.
remote: Compressing objects: 100% (36/36), done.
remote: Total 43 (delta 10), reused 31 (delta 5)
Unpacking objects: 100% (43/43), done.
From https://github.com/paulboone/ticgit
 * [new branch]      master     -> pb/master
 * [new branch]      ticgit     -> pb/ticgit
```

La rama maestra de Paul ahora es accesible localmente con el nombre `pb/master` - puedes combinarla con alguna de tus ramas, o puedes crear una rama local en ese punto si quieres inspeccionarla.



3. **Replicar un repositorio local en un servidor remoto.**

Cuando tienes un proyecto que quieres compartir, debes enviarlo a un servidor. El comando para hacerlo es simple: `git push [nombre-remoto] [nombre-rama]`. Si quieres enviar tu rama `master` a tu servidor `origin`
 (clonar un repositorio establece esos nombres automáticamente), entonces puedes ejecutar el siguiente comando y se 
enviarán todos los *commits* que hayas hecho al servidor:

`$ git push origin master`

Este comando solo funciona si clonaste de un servidor sobre el que  tienes permisos de escritura y si nadie más ha enviado datos por el  medio. Si alguien más clona el mismo repositorio que tú y envía información antes que tú, tu envío será rechazado. Tendrás que traerte su trabajo y combinarlo con el tuyo antes de que puedas enviar datos al servidor.


4. **Traer los cambios de un repositorio remoto a un repositorio local.**

Para obtener datos de tus proyectos remotos puedes ejecutar: `$ git fetch [remote-name]`

El comando comunica con un repositorio remoto y obtiene toda la información que se encuentra en ese repositorio que no está en el tuyo actual y la almacena en tu base de datos local. Luego de hacer esto, tendrás referencias a todas las ramas del remoto, las cuales puedes combinar e inspeccionar cuando quieras.

Si clonas un repositorio, el comando de clonar automáticamente añade ese repositorio remoto con el nombre “origin”. Por lo tanto, `git fetch origin` se trae todo el trabajo nuevo que ha sido enviado a ese servidor desde que lo clonaste (o desde la última vez que trajiste datos).
Es importante destacar que el comando `git fetch` solo trae datos a tu repositorio local 
(ni lo combina automáticamente con tu trabajo ni modifica el trabajo que llevas hecho), la combinación con tu trabajo debes hacerla manualmente.

Si has configurado una rama para que rastree una rama remota, puedes usar el comando `git pull` para traer y combinar automáticamente la rama remota con tu rama actual. Por defecto, el comando `git clone` le indica automáticamente a tu rama maestra local que rastree la rama maestra remota (o como se llame la rama por defecto) del servidor del que has clonado. Generalmente, al ejecutar `git pull` traerás datos del servidor del que clonaste originalmente y se intentará combinar automáticamente la información con el código en el que estás trabajando: es básicamente una combinación de los comandos `git fetch` y `git merge`, donde Git descargará desde el repositorio remoto especificado y, a continuación, de forma inmediata intentará combinarlo en la rama en la que te encuentres.


5. **Resolver los conflictos que se puedan producir al traerse estos cambios**.

Es común que los sistemas de control de versiones gestionen las contribuciones de varios autores. A veces, varios desarrolladores pueden intentar editar el mismo contenido: si el desarrollador A intenta editar el código que el desarrollador B está editando, puede producir un conflicto**.** Para disminuir la aparición de conflictos, los desarrolladores deben trabajar en ramas separadas y aisladas. ****El comando `git merge` tiene como responsabilidad principal combinar ramas separadas y resolver cualquier edición en conflicto.

Aun así, los conflictos usualmente se crean cuando dos desarrolladores han cambiado las mismas 
líneas en un archivo, o si un desarrollador eliminó un archivo mientras otro lo estaba modificando. En estos casos, Git no puede determinar automáticamente qué es correcto, por lo que hay que solucionarlos manualmente (realmente, los conflictos solo afectan al desarrollador que realiza la fusión).

A la hora de hacer el *merge*, si hay conflictos git nos dirá qué archivo es el afectado y será mostrado con algo como:

```jsx
Auto-merging index.html
CONFLICT (content): Merge conflict in index.html
Automatic merge failed; fix conflicts and then commit the result.
```

El archivo se mostrará tal que así:

![Untitled](Git%20d2395b8688ee4f0180604699e79ff39b/Untitled.webp)

La forma más directa de resolver un conflicto es editar el archivo generado: hay que abrir el archivo afectado y eliminar manualmente todos los divisores de conflicto (en el ejemplo, elegir el código que nos interese que esté entre `<<<<<<< HEAD` y `=======` o `======` y `>>>>>>> contenido`)**.** Una vez que se haya editado el archivo, hacer `git commit -a`.


6. **Enviar los cambios de un repositorio local a uno remoto.**

Cuando tienes un proyecto que quieres compartir, debes enviarlo a un servidor. El comando para hacerlo es simple: `git push [nombre-remoto] [nombre-rama]`. Si quieres enviar tu rama `master` a tu servidor `origin` (recuerda, clonar un repositorio establece esos nombres automáticamente), entonces puedes ejecutar el siguiente comando y se enviarán todos los *commits* que hayas hecho al servidor: `$ git push origin master`

Este comando solo funciona si clonaste de un servidor sobre el que tienes permisos de escritura y si nadie más ha enviado datos por el medio. Si alguien más clona el mismo repositorio que tú y envía información antes que tú, tu envío será rechazado. Tendrás que traerte su trabajo y combinarlo con el tuyo antes de que puedas enviar datos al servidor.


7. **Enviar una rama local al repositorio remoto.**

Cuando quieres compartir una rama con el resto del mundo, debes llevarla (push) a un remoto donde tengas permisos de escritura. Tus ramas locales no se sincronizan automáticamente con los remotos en los que escribes, sino que tienes que enviar (push) expresamente las ramas que desees compartir.

Si tienes una rama llamada `serverfix`, con la que vas a trabajar en colaboración; puedes llevarla al remoto de la misma forma que llevaste tu primera rama: con el comando `git push (remoto) (rama)` .

```jsx
$ git push origin serverfix
Counting objects: 24, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (15/15), done.
Writing objects: 100% (24/24), 1.91 KiB | 0 bytes/s, done.
Total 24 (delta 2), reused 0 (delta 0)
To https://github.com/schacon/simplegit
 * [new branch]      serverfix -> serverfix
```

NOTA: *Git expande automáticamente el nombre de rama `serverfix` a `refs/heads/serverfix:refs/heads/serverfix`, que significa: “coge mi rama local `serverfix` y actualiza con ella la rama `serverfix` del remoto”. También puedes hacer `git push origin serverfix:serverfix`, que hace lo mismo; es decir: “coge mi `serverfix` y hazlo el `serverfix` remoto”. Puedes utilizar este último formato para llevar una rama local a una rama remota con un nombre distinto. Si no quieres que se llame `serverfix` en el remoto, puedes lanzar, por ejemplo, `git push origin serverfix:awesomebranch`; para llevar tu rama `serverfix` local a la rama `awesomebranch` en el proyecto remoto.*

La próxima vez que tus colaboradores recuperen desde el servidor, obtendrán bajo la rama remota `rigin/serverfix` una referencia a donde esté la versión de `serverfix` en el servidor:

```jsx
$ git fetch origin
remote: Counting objects: 7, done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 3 (delta 0)
Unpacking objects: 100% (3/3), done.
From https://github.com/schacon/simplegit
 * [new branch]      serverfix    -> origin/serverfix
```

Es importante destacar que cuando recuperas (*fetch*) nuevas ramas remotas, no obtienes automáticamente una copia local editable de las mismas: no tienes una nueva rama `serverfix` , sino que únicamente tienes un puntero no editable a `origin/serverfix`. Para integrar (*merge*) esto en tu rama de trabajo actual, puedes usar el comando `git merge origin/serverfix`, y si quieres tener tu propia rama `serverfix` para trabajar, puedes crearla directamente basándote en la rama remota:

```jsx
$ git checkout -b serverfix origin/serverfix
Branch serverfix set up to track remote branch serverfix from origin.
Switched to a new branch 'serverfix'
```


8. **Incorporar a ramas locales cambios que se producen en el repositorio remoto.**

La forma más sencilla de actualizar nuestro repositorio local con los posibles cambios que se hayan podido producir en el repositorio remoto es mediante el comando `git pull`. Si existen cambios éstos se descargarán y se fusionarán con nuestros cambios locales automáticamente, aunque pueden ocurrir errores:

![Untitled](Git%20d2395b8688ee4f0180604699e79ff39b/Untitled.png)

Este error ocurre porque una rama local de nuestro repositorio no tiene asignada una rama del repositorio remoto. Podremos especificar a qué rama remota corresponde la rama local con el comando `git branch --set-upstream-to=origin/master master` . Si no hay errores, deberíamos obtener una pantalla similar a ésta: 

![Untitled](Git%20d2395b8688ee4f0180604699e79ff39b/Untitled%201.png)

Usando el comando `git log` podremos ver los cambios que se han efectuado.

Realmente, al hacer `git pull` los cambios se descargan y fusionan automáticamente. Si lo que buscamos es realizar los cambios de manera manual, tendremos que utilizar la combinación de `git fetch` y `git merge` . Al hacer el *fetch*, los cambios se quedarán en una nueva rama llamada origin/master. Para aplicar dichos cambios tendremos que utilizar `git merge origin/master`.

  

9. **Realizar un pull request entre dos ramas de un repositorio remoto.**

Un *pull request* es una petición que hace el desarrollador de una rama para que sus cambios se fundan con la rama principal. No es una operación *git* propiamente dicha, sino un servicio que ofrecen los servidores (GitLab o GitHub).

Para actualizar/sincronizar nuestros cambios con una rama maestra empezamos por agregarlos, hacer el *commit* y un último *push* de esa rama:

```jsx
$ git add --all
$ git commit -m "actualizacion"
$ git push -u origin index-page
```

En el ejemplo, hemos utilizado la rama ‘*index-page*’ para hacer el *push* en vez del master. Esto lo hacemos así para hacer un *pull request* más estructurado.

Ahora al ir a la página del repositorio en GitHub, en el menú de ramas ‘*Branch:*’ aparecerá la nueva rama ‘*index-page*’:

![Untitled](Git%20d2395b8688ee4f0180604699e79ff39b/Untitled%202.png)

Al clicar la rama podremos darle al botón ‘*Compare & pull-request*’, el cual permite hacer el *pull* a la rama inicial. Podemos hacer una descripción de qué vamos a subir y, cuando terminemos, pulsamos en ‘*Create pull request*’. Ya solo falta que el master apruebe el *pull request*.
