# Curso de Introducción a la Terminal y Linea de Comandos

[Listado de comandos](https://static.platzi.com/media/public/uploads/command-line-cheat-sheet_f2552bde-3bb0-4b1c-a1a7-dbd40095fa4f.pdf)

## ¿Qué es la terminal? 

Es una herramienta indispensable para los desarrolladores y estas son las razones

1. Tiene mucha **flexibilidad,** con unos cuantos comandos bien escritos y estructurados podemos ejecutar procesos en nuestras computadoras de una manera eficaz. \(Mover archivos, hacer copias, backups, o implementar procesos que se ejecuten de forma automática cada cierto tiempo\)
2. Hacer los procesos desde terminal tiende a ser mucho más **rápido** que si lo hacemos de forma habitual mediante una interfaz grafica 
3. No siempre tenemos disponible una interfaz grafica, existen muchos casos de uso, por ejemplo al configurar un servidor remoto.
4. Si no sabemos usar la terminal de forma correcta podemos invocar demonios.

La terminal es una interfaz grafica que simula una linea de comandos , es decir, la terminal es la ventana que aloja la shell o linea de comandos, esta es un programa que toma los comandos y los pasa al SO para que realice determinada acción.

#### Tipos de Shell

* Bourne Shell
* Bash Shell \(Linux\)
* Z Shell \(Mac\)
* C Shell
* Korn Shell
* Fish Shell
* PowerShell \(Windows\) 

{% hint style="info" %}
Un comando es un programa que se puede ejecutar desde la terminal.
{% endhint %}

## Aprendiendo a caminar en la terminal

### Sistema de archivos

![](../.gitbook/assets/image%20%2814%29.png)

> En la carpeta 📁 `home` se encuentran los usuarios del SO.

### Comandos Básicos

| Comando | Descripción |
| :--- | :--- |
| `ls` | Lista los archivos y directorios. |
| `ls -l` | Lista los archivos con toda su info |
| `ls -lh` | Lista los archivos con toda su info legible para los humanos |
| `ls -la` | Lista los archivos incluso los archivos ocultos |
| `ls -lS` | Lista los archivos y los ordena por peso |
| `ls -lr` | Lista los archivos en orden alfabético inverso |
| `tree` | Lista los archivos en visualización de árbol |
| `tree -L {#}` | Visualización en árbol a la profundización indicada |
| `cd` | Se traslada a`home` |
| `cd {folder}` | Se traslada a `/folder` |
| `clear` o `ctrl+L` | Limpia la consola |
| `pwd` | Imprime la ruta en la cual nos encontramos posicionados |
| `file {archivo}` | Describe el tipo de archivo que le pasamos como parámetro |

### Rutas

* Rutas absolutas: Son las rutas que especifican puntualmente una dirección ej : `home/kathe/Platzi/`
* Rutas relativas: Son rutas que pueden variar dependiendo de la dirección en la que estemos. 
  * `.` Esta ruta se refiere a la dirección actual
  * `..` Esta ruta se refiere a al directorio que contiene la ruta actual

## Manipulando archivos y directorios

| Comando | Descripción |
| :--- | :--- |
| `mkdir {folder}` | Creación de directorio |
| `touch {file}` | Creación de archivos |
| `cp {origin_file} {new_file}` | Copiar archivo en el mismo folder |
| `mv {file} {path}` | Mover un archivo a otro folder |
| `mv {name_file} {new_name_file}` | Renombrar un archivo |
| `rm {archivo}` | Eliminar un archivo |
| `rm -i {archivo}` | Elimina el archivo de forma intuitiva |
| `rm -r {folder}` | Eliminar un directorio |

## Explorando el contenido de nuestros archivos

| Comando | Descripción |
| :--- | :--- |
| `head {archivo}` | Visualiza las 10 primeras líneas del archivo |
| `head {archivo} -n {#}` | Visualiza las primeras \# líneas del archivo |
| `tail {archivo}` | Visualiza las 10 ultimas líneas del archivo |
| `tail {archivo} -n {#}` | Visualiza las ultimas \# líneas del archivo |
| `less {archivo}` | Visualiza el srchivo e internamente permite la busqueda de palabras |
| `xdg-open {archivo}` | Abre el archivo con el programa predeterminado  |
| `nautilus {ruta}` | Abre el explorador de archivo con la ruta indicada |

## ¿Qué es un comando?

Un comando puede ser lo siguiente:

1. Un programa executable `mkdir`
2. Un comando de utilidad para la shell `cd`
3. Una función de shell 
4. Un alias `ls`

> 🔔 `type {comando}` Nos indica la naturaleza del comando como parámetro

### Crear un alias

Para crear un alias vamos usar la palabra reservada alias. `alias new_command = "{command}"`

> ⚠Los comandos que creemos se borraran una vez cerremos la terminal en donde se crearon

### Comandos informativos

| Comando | Descripción |
| :--- | :--- |
| `help {command}` | Visualiza info sobre como usar el comando. |
| `man {command}` | Visualiza el manual de usuario del comando |
| `info {command}` | Visualiza el manual de usuario del comando de forma breve |
| `whatis {command}` | Descripción muy corta de que hace el comando |

## Wildcars

Son una serie de caracteres especiales que nos permiten realizar búsquedas mucho más avanzadas.

| Comando | Descripción |
| :--- | :--- |
| `ls *.txt` | Filtra por los archivos de la extensión `.txt` |
| `ls datos*` | Filtra por los archivos que empiezan con el nombre `datos` |
| `ls datos?` | Filtra por los archivos que empiezan con`datos` pero tiene **una** sola coincidencia |
| `ls datos???` | Filtra por los archivos que empiezan con`datos` pero tiene **tres** coincidencias |
| `ls [[:upper:]]*` | Filtra por los archivos que empiezan con mayúscula hasta dos niveles del árbol |
| `ls -d [[:upper:]]*` | Filtra por los archivos que empiezan con mayúscula en el **mismo directorio** |
| `ls [[:lower:]]*` | Filtra por los archivos que empiezan con minúscula |
| `ls [ab]*` | Filtra por los archivos que empiezan por **a y b** |

## Redirecciones: cómo funciona la shell

En el diagrama vemos el standar input \(`stdin`\) que proviene del teclado pero también puede ser redirigido desde archivos de texto.

![](../.gitbook/assets/image%20%2815%29.png)

> 🔔 A los \# de los std se les conoce como **file descriptors.**

Cuando el `stdin->(0)` entra dentro de nuestro comando puede resultar dos cosas, un `stdout->(1)` o un `stderr->(2)` y ambas salidas se manejan de forma distinta y así los interpreta la shell.

| Standar | file descriptor | operator | variant |
| :--- | :--- | :--- | :--- |
| stdin | 0 | &gt; | &gt;&gt; |
| stdout | 1 | &lt; |  |
| stderr | 2 | 2 |  |

### Comandos de la clase

| Comando | Descripción |
| :--- | :--- |
| `ls {folder} > {archivo}` | Crea el archivo y almacena el `stdout` en el archivo |
| `ls {folder} >> {archivo}` | No sobreescribe el archivo, concatena con lo que tenga almacenado |
| `ls {folder} 2> {archivo}` | Si se genera un error, redirige el `stderr` al archivo |
| `ls {folder} > {archivo} 2>&1` | Redirige el`stderr` o el `stdout` según lo que genere la ejecución del comando |

## Redirecciones: pipe operator

El _`pipe operator`_`|`  permite pasar el `stdout` de un comando al `stdin` de otro comando, esto permite generar filtros, encadenamientos o funcionalidades. Ej: `ls -lh | less`

| Comando | Descripcion |
| :--- | :--- |
| `echo "Hola mundo"` | Imprime en consola `"Hola mundo"` |
| `cat {archivo}` | Imprime en consola el contenido del archivo |
| `ls | tee {archivo} | less` | Redirecciona el `stdout` al archivo y visualiza con `less` |
| `ls | sort` | Ordena el `stdout` de `ls` |

## Encadenando comandos: operadores de control

Son símbolos reservados por la terminal que permiten ejecutar más de un comando o encadenarlos, podemos ejecutarlos síncronamente, asíncronamente e incluso con condicionales.

### Síncrono

Para indicar que los comandos se ejecuten de forma síncrona se usa el operador `;`

`ls; mkdir {folder}; cal`

### Asíncrono

Para indicar que los comandos se ejecuten de forma asíncrona se usa el operador `&`

`ls & date & cal`

### Condicional

* `mkdir {folder} && cd {folder}` 
* `cd {folder} || echo "Hola Mundo"`

## Cómo se manejan los permisos

### Tipos de archivos

| Atributo | Tipo de archivo |
| :--- | :--- |
| - | Un archivo normal |
| d | Un directorio |
| l | Un link simbólico |
| d | Un archivo de bloque especial. Son archivos que manejan la información de los bloques de datos como una USB |

### Tipo de modo

* Dueño: La persona que crea el archivo **\(rwx\)**
* Grupo: Puede ser compartido entre diferentes usuarios \(r-x\)
* World: Cualquiera que no entre en la categoría de dueño o grupo **\(r-x\)**

#### Diferencia de permisos entre archivos y directorios

| Permiso | Archivo | Directorio |
| :--- | :--- | :--- |
| r | Permite abrir y leer un archivo. | Permite listar el contenido de un directorio solo si el permiso de ejecución \(x\) también está activo. |
| w | Permite escribir en un archivo; sin embargo, este atributo no permite cambiar el nombre de los archivos o eliminarlos. La capacidad de eliminar o cambiar el nombre de los archivos está determinado por los atributos del directorio. | Permite que los archivos dentro de un directorio sean creados, eliminados y renombrados si también se establece el atributo de ejecución. |
| x | Permite que un archivo sea tratado como un programa y pueda ser ejecutado. | Permite entrar al directorio |

### Modo Octal

![](../.gitbook/assets/image%20%2817%29.png)

### Modo Simbólico

![](../.gitbook/assets/image%20%2816%29.png)

## Modificando permisos en la terminal

El usuario `root` tiene privilegios para hacer prácticamente todo y por esto debemos aprender a manejarlo de forma adecuada. 

Para modificar los permisos de un archivo o directorio usamos `chmod`

* Cambiando permisos en modo octal: `chmod 755 {archivo}`
* Quitando permiso de lectura al usuario con modo simbólico: `chmod u-r {archivo}` 
* Añadiendo permiso de lectura al usuario con modo simbólico: `chmod u+r {archivo}` 
* Quitar permiso de ejecución al usuario y añadiendo permiso de escritura al grupo y al resto: `chmod u-x,go=w {archivo}` 
* \`\`

### Comandos de la Clase

| Comando | Descripción |
| :--- | :--- |
| `whoami` | Nos dice que usuario somos |
| `id` | Nos dice el `uid` que es el sistema de nuestro usuario, además nos da información de que otros grupos podemos pertenecer. |
| `su {usuario}` | Realiza el Switch User que nos permite cambiar entre los usuarios que tengamos registrados |
| `sudo` | Nos permite hacer acciones de `root` |
| `passwd` | Nos permite cambiar la contraseña |

## Variables de entorno

### Comandos de la clase

| Comando | Descripción |
| :--- | :--- |
| `prinenv` | Nos muestra todas las variables de entorno que tenemos configuradas |
| `echo ${variable_entorno}` | Imprime el contenido de la variable |

En `.bashrc` es el archivo que contiene toda la configuración, variables y alias lo encontramos como

#### Bonus - Crear un link simbólico

`ls -s {PATH} {name_link}`

## Comandos de Búsqueda

Nos ayudan a encontrar archivos o directorios y podemos filtrarlos dependiendo su extensión, su nombre, su ubicación etc.

{% hint style="info" %}
Esto es realmente util cuando queremos encontrar archivos `.log`  los cuales son archivos de texto plano que recopilan la información de un archivo en ejecución.
{% endhint %}

### Comandos de la clase

| Comando | Descripción |
| :--- | :--- |
| `which {bin}` | Nos muestra la ruta donde se almacena el binario |
| `find {patch} -name {name}` | Busca los files con el nombre indicado en la ruta indicada |
| `find {path} -type d -name {name}` | Busca los directorios \(d\) con el nombre y la ruta indicada  |
| `find {path} -type f -name *.log` | Busca los archivos \(f\) .log en la ruta indicada |
| `find {patch} -size 20M` | Busca los archivos que pesen más de 20Mb |

## Grep

Nos permite encontrar coincidencias de una búsqueda dentro de un archivo .txt  o en general de cualquier texto, por ejemplo un `stdout` 

* Encontrar las coincidencias de un archivo:  
  * `grep {expReg} {file}`

| Opciones de grep | Descripción |
| :--- | :--- |
| `-i` | No case sensitive |
| `-c` | Número de coincidencias |
| `-v` | \#de no coincidencias |

`Ejemplo: grep -v {expReg} {file}`

#### Bonus : Contador wc

`Ejemplo: wc {file}`   -&gt; Contador de palabras, letras, bits

| Opciones de wc | Descripción |
| :--- | :--- |
| `-l` | Cuenta las líneas |
| `-w` | Cuenta las palabras |
| `-c` | Cuenta los bits |

## Utilidades de Red

* **`ifconfig`**sirve para ver la mascara de red, puerto de transmisión, tarjeta de red, etc
* **`ping`**nos muestra si una ip o pagina, esta activa, si salen paquetes es porque hay conexión.
*  **`curl pagina_web`** podemos traer el html de una pagina, podríamos guardarlo con el estándar output.
* **`wget pagina_web`** nos descarga el archivo html, pero con formato.
* **`traceroute pagina_web`**nos sirve para ver por cuales computadoras tenemos que ir pasando para llegar por ejemplo a una pagina web. Ejemplo, nos saldrán las ip que tenemos que pasar para llegar a la pagina que queremos.
* **`netstat –i`** nos muestra los dispositivos de red.

## Comprimiendo archivos

| Comando  | Descripción |
| :--- | :--- |
| `tar -cvf {name}.tar {file}` | Comprime el archivo en formato tar -&gt; c: comprimir, v:ver en terminal, f:file |
| `tar -cvzf {name}.tar.gz {file}` | Comprime el archivo con el algoritmo `gzip` -&gt; z |
| `tar -xvzf {folcer}.tar.gz` | Descomprime el archivo -&gt; x:descomprimir |
| `zip -r {name}.zip {folder}` | Comprime en formato `.zip` |
| `unzip {name}.zip` | Descomprime un archivo `.zip` |

## Manejo de Procesos

| Comando  | Descripción |
| :--- | :--- |
| `ps` | Muestra los procesos corriendo en nuestra terminal. Todo proceso tiene un ID. |
| `kill {PID}` | Mata un proceso con el ID del proceso |
| `top` | Muestra los procesos que están usando más recursos. |

