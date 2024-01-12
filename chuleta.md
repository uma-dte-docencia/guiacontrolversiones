# **Chuleta de control de versiones con git**

## 1. Definiciones

* **Control de versiones**: El control de versiones es un sistema que registra los cambios realizados sobre un archivo o conjunto de archivos a lo largo del tiempo, de modo que puedas recuperar versiones específicas más adelante

* **Conceptos:**
    *  **Repositorio local**: Es una base de datos centralizado donde se guardan las distintas versiones de los ficheros sometidos a control de versiones.

    * **Copia local**: Es la copia que hacen los usuarios de un fichero sometido a control de versiones. El **DIRECTORIO LOCAL (working directory/working tree/workspace)** es el que contiene todas las copias locales. 

    * **Repositorio remoto**: Es una base de datos centralizada donde se guardan las distintas versiones de los ficheros sometidos a control de versiones, y reside en el servidor centralizado. 
* **Index o Stage (zona de preparación)**: contiene todos los ficheros preparados.	

***FICHERO PREPARADO (staged file)***: Es la copia del fichero modificado preparada para ser confirmada en la próxima operación de confirmación (COMMIT).
* ***Log***:  Registro de todos los cambios que se han producido en el repositorio. Es responsabilidad del cliente añadir información al log cuando se produce un cambio. También llamado histórico.
* **Conflicto**: Problema que surge cuando los clientes realizan cambios incompatibles entre sí.
    
* **Operaciones**:
    * **Clone**: Realiza una copia de un repositorio remoto en un directorio local.
    
    * **Add**: Añade un archivo al siguiente commit.
    
    * **Commit**: Confirma los cambios en el repositorio local.
    * **Merge (fusionar)**: Traslada los cambios de una rama a otra.
    
    * **Rebase (reorganización/trasplantar) **: Trasplanta sobre un tronco que ha crecido después de crear la rama.

    * **Push**: Envía al repositorio remoto los cambios correspondientes a los commits realizados desde el último push.
    
    * **Pull**: Descarga desde el repositorio remoto los archivos actualizados en commits que hayan realizado otros usuarios, y los integra (realiza un merge) con el repositorio local.
    
    * **Fork**: Crear una copia de un repositorio. Esto es especialmente útil para modificar proyectos sin afectar al proyecto original.
    
    * **Pull Request**: Petición de un pull, para que un nivel superior a una rama u otra rama distinta incorpore cambios (commits) de esta.
    
* **Servicios de repositorio remoto**: GitHub, GitLab, BitBucket, etc.

* **Clientes gráficos para el control de versiones**: gitg, gitkraken, gitblade, etc.

## 2. Comandos

Consideraciones generales:
* **\*** : es sustituido por una lista con todos los nombres de lo ficheros del directorio actual.
* **..** : directorio padre.

### 2.1. Comandos básicos del terminal

Comando    | Argumentos              | Función 
-----------|-------------------------|------------
**pwd**    |                         | Muestra el directorio actual (Print Working Directory).
**mkdir**  | &lt;dir>                | Crea un directorio.
**cd**     | &lt;dir>                | Cambia de directorio (*'cd -': directorio previo*).
**ls**     | [-l] [-a]               | Muestra los archivos del directorio *(l: detallado; a: incluye ficheros ocultos).*
**rm**     | &lt;file>               | Elimina un fichero.
**mv**     | &lt;source> &lt;dest>   | Mueve o renombra un archivo.


### 2.2. Control de versiones local

Comando        | Argumentos         | Función 
---------------|--------------------|------------
**git init**   |                    | Crea un repositorio local en el directorio actual.
**git add**    | &lt;file>          | Prepara ficheros para ser confirmados en un repositorio local.
**git commit** | [-m &lt;message>]  | Confirma cambios en un repositorio local. *(m: permite escribir el mensaje del commit sin abrir el editor de texto).*
**git diff**   | &lt;file>          | Muestra los cambios de un archivo "modificado" con respecto al que hay en el repositorio.
**git reset**  | [--soft]           | Deshace el add. *(soft: deshace el commit)*
**git status** |                    | Muestra el estado actual del repositorio.


### 2.3 Control de versiones centralizado

Comando        | Argumentos                                      | Función 
---------------|-------------------------------------------------|------------
**git config** | [--global][--local] http.proxy &lt;domain:port> | Configura distintos aspectos de git, en todo el PC o en el repositorio actual. Por ejemplo, el servidor proxy.
**git clone**  | &lt;URL>                                        | Realiza una copia de un repositorio remoto en un directorio local.
**git remote** | add &lt;URL>                                    | Enlaza nuestro repositorio local con un repositorio remoto, donde se subirán los cambios al realizar push.
**git pull**   | &lt;remote> &lt;branch>                         | Descarga los archivos actualizados del repositorio remoto y realiza un merge entre el repositorio local y el remoto.
**git merge**  | &lt;branch>                                     | Incorpora los cambios  realizados en los commits de otra rama al repositorio local.
**git push**   | &lt;remote> &lt;branch>                         | Actualiza el repositorio remoto con los cambios realizados en los commits locales que se han realizado desde el último push.


### 2.4 Control de versiones distribuido

Comando              | Argumentos                   | Función 
---------------------|------------------------------|------------
**git branch**       | &lt;branch_name>             | Crea una rama nueva en el repositorio local.
**git checkout**     | &lt;branch_name>             | Cambia de rama en el repositorio local.
**git push**         | [-u] &lt;remote> &lt;branch> | Envía la rama al repositorio remoto.

Operaciones de Github:

Operacion                                 | Descripción
------------------------------------------|------------
**pull request** (entre ramas)            | En la página principal del repositorio: "New pull request" y se selecciona la rama deseada
**pull request** (entre repositorios)     | Dentro de la misma opción anterior, seleccionando: "compare across forks"

## 3. Uso del formato .md (A partir de aquí son cosas útiles que no entran en la guía de estudio de la asignatura, pero que ayudan a escribir este tipo de documento)

### 3.1 Definición

El **Markdown** es un lenguaje de marcado con sintaxis en texto plano para generar textos con formato.

Los archivos en Markdown se guardan con la extensión <code class="language-plaintext highlighter-rouge">.md</code> y se pueden abrir en cualquier editor de texto. 

### 3.2 Uso del lenguaje Markdown

#### 3.2.1 Encabezados

Markdown dispone de cuatro niveles de encabezados definidos por el número de <code class="language-plaintext highlighter-rouge">#</code> antes del texto del encabezado.

| Caracter  | Definición                    |
|----------:|-------------------------------|
| #         | Primer nivel de encabezado    |
| ##        | Segundo nivel de encabezado   |
| ###       | Tercer nivel de encabezado    |
| ####      | Cuarto nivel de encabezado    |

#### 3.2.2 Párrafos y saltos de línea

Los párrafos son simplemente texto plano escrito sin ninguna peculiaridad propia del lenguaje, para escribir un párrafo simplemente teclea como lo haría en un archivo <code class="language-plaintext highlighter-rouge">.txt</code>. 
<br><br><br><br>
De igual modo, para un salto de línea simplemente hay que introducir <code class="language-plaintext highlighter-rouge">< br ></code> como se haría normalmente en **HTML**. Este párrafo por ejemplo, tiene cuatro saltos de línea de separación en lugar de uno con respecto al anterior.

#### 3.2.3 Negrita y cursiva

El texto se puede poner en cursivas encerrándolo entre los símbolos <code class="language-plaintext highlighter-rouge">*</code> o <code class="language-plaintext highlighter-rouge">-</code>. De la misma forma, el texto en negritas se escribe encerrando la palabra entre <code class="language-plaintext highlighter-rouge">**</code> o <code class="language-plaintext highlighter-rouge">__</code>.

* **Ejemplo de texto en negrita**
* *Ejemplo de texto en cursiva*

#### 3.2.4 Listados

Markdown soporta la creación de listas ordenadas y sin ordenar.

Para la creación de una lista sin orden simplemente debemos utilizar el caracter <code class="language-plaintext highlighter-rouge">*</code> delante del parráfo o línea que queramos listar y un espacio entre el caracter y el texto y, para crear distintos niveles solo tenemos que aumentar la sangría de las líneas. Es tan sencillo como se muestra a continuación:

* Padre
    * Hijo 1
    * Hijo 2
    * Hijo 3
* Madre

Para listas ordenadas es tan sencillo como listar mediante números y un punto, como se muestra a continuación:

1. tarea 1
2. tarea 2
3. tarea 3

#### 3.2.5 Fragmentos de código

Dado que Markdown no distingue las tipografías involucradas los fragmentos de código se representan encerrados entre dos signos de acento grave <code class="language-plaintext highlighter-rouge">`</code>. Y cuando queramos representar un bloque completo de código lo debemos encerrar entre dos líneas de tres acentos graves. 

```
...
Fragmento de código
...
```

#### 3.2.6 Bloques de citas

Los bloques de citas se representan usando el caracter <code class="language-plaintext highlighter-rouge">></code> delante del párrafo que queramos convertir en un bloque de citas. Como se muestra a continuación:

> Éste es un párrafo de texto incluido como un bloque de cita

#### 3.2.7 Bloques de citas

Se pueden mostrar imágenes mediante el uso del caracter <code class="language-plaintext highlighter-rouge">!</code>, seguido de un texto alternativo entre corchetes, seguido a su vez por el URL de la imagen y un título opcional entre comillas.

![Foto de ejemplo](https://media-exp1.licdn.com/dms/image/C4D03AQFNqIfFGUsLFg/profile-displayphoto-shrink_800_800/0/1574444201467?e=1654128000&v=beta&t=dmmHEevV7WN1XyVcIfAkDJ2502Rlwf5LQMDiNry8nyo "Mi foto")

#### 3.2.8 Enlaces o hipertexto

El título del enlace se encierra primero entre corchetes y después se incluye la dirección completa del URL entre paréntesis.

[Mi GitHub](https://github.com/FranciscoJoseLara)

#### 3.2.9 Líneas horizontales

Puedes incluir líneas horizontales si escribes en una misma línea cualquiera de los siguientes tres signos: <code class="language-plaintext highlighter-rouge">-</code>, <code class="language-plaintext highlighter-rouge">*</code> o <code class="language-plaintext highlighter-rouge">_</code>, sin importar los espacios que dejes entre ellos. Cualquiera de estas combinaciones generarán una línea horizontal como las siguientes:

---
***
___

#### 3.2.10 Tablas

La versión básica de Markdown no incluye tablas, sin embargo, algunos sitios web y aplicaciones usan variantes de Markdown que pueden incluir tablas y otras características especiales. Para crear una tabla en GitHub, usa barras verticales <code class="language-plaintext highlighter-rouge">|</code> para separar columnas y guiones entre los encabezados y el resto del contenido de la tabla.

|        | Encabezado A | Encabezado B |
|--------|--------------|--------------|
| Fila 1 | 1,1          | 1,2          |
| Fila 2 | 2,1          | 2,2          |
| Fila 3 | 3,1          | 3,2          |

Para especificar la alineación del contenido de cada columna se pueden agregar dos puntos <code class="language-plaintext highlighter-rouge">:</code> al renglón de los encabezados:

|        | Encabezado A | Encabezado B |
|:-------|:------------:|-------------:|
| Fila 1 | 1,1          | 1,2          |
| Fila 2 | 2,1          | 2,2          |
| Fila 3 | 3,1          | 3,2          |

### Referencias de las sección 3

* Referencia: [Programming Historian](https://programminghistorian.org/es/lecciones/introduccion-a-markdown) Es responsabilidad del cliente añadir información al log cuando se produce un cambio. 
