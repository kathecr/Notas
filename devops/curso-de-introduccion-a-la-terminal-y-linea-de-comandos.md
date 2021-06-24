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

