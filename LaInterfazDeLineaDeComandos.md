---
title: "Sistemas operativos Linux y la Intrefaz de Línea de Comandos"
subtitle: "Sesión práctica"
author: "Patricia Carvajal-López"
date: "24/10/2021"
note: "Documento de soporte del tutorial "Sistemas operativos Linux y la Interfaz de Líneas de Comandos" (_CLI - Command Line Interface_)

---

___
# Sistemas operativos Linux y la Intrfaz de Línea de Comandos (CLI - Command Line Interface)
___
Documento de soporte de la sección práctica del tutorial Sistemas operativos Linux y la Intrfaz de Línea de Comandos (CLI - Command Line Interface) [registro Zenodo de archivos para la práctia](https://doi.org/10.5281/zenodo.5550981)
<p>&nbsp;</p>

__Algunas notas antes de iniciar.__ 
* Al dar el comando `clear` su teminal de Linux se limpiará.
* Al pulsar la tecla 'Tab' puede ayudarle a rellenar automáticamente nombres de comandos archivos o directorios.
* Las flechas arriba y abajo le ayudaran a traer comandos escritos previamente en la terminal
* Tiene muchas opciones para solicitar yuda sobre los comandos de LINUX, por ejemplo:
* `command -h` despliega la página de ayuda del comando
* `command -help` tambien despliega la página de ayuda del comando
* `man command` le llevará al manual del comando (pulse `q` una vez que quiera salir del manualnual)
*   La Interfaz de Líneas de Comandos (_Command Line Interface_, o CLI por su nombre y siglas en inglés) también es conocida como 'Terminal' o 'Shell'

<p>&nbsp;</p>

##  Preparación para la práctica

Para equipos con sistemas Linux abra la Terminal y de entrada a los siguientes comandos:
```
cd ~/
wget http://zenodo.org/record/5594996/files/practica-cli.tar.gz
tar -xvzf practica-cli.tar.gz
ls
clear
cd practica-cli
```

Para equipos Mac
```
cd ~/
curl http://zenodo.org/record/5594996/files/practica-cli.tar.gz -o practica-cli.tar.gz 
tar -xvzf practica-cli.tar.gz
ls
clear
cd practica-cli
```
<p>&nbsp;</p>

## 1. Variables ambientales  

El comando `echo` es utilizado para desplegar líneas de texto o cadenas que le son indicadas por medio de argumentos de entrada. Por ejemplo, si en su Terminal usted escibe
```
echo La puerta está cerrada
```
Usted literalmente vera en su terminal un mensaje que dirá "La puerta está cerrada"

Ahora utilizemos el comando `echo` para visualizar el valor de un par de variables ambientales.

Visualice la ruta de archivo del 'directorio por defecto' de su sistema, el cual es llamado 'home'. Esta ruta esta contenida en la variable de ambiente _HOME_
```
echo $HOME
```
Ahora visualice en su terminal el contenido de la variable _PATH_. Esta variable contiene todos las rutas absolutas de los directorios donde se encuentran archivos ejecutables. Si la ruta de algun programa no se encuentra contenida en esta variable tendrá que indicarle al sistema donde se encuentra su archivo ejecutable y adherir un punto antes de correr un programa; el ejemplo del tutorial lo mostró al tratar de correr el programa `./programita.sh`

```
echo $PATH
programita.sh
./programita.sh
```

En preparación de nuestro siguientes pasos de la práctica demos la entrada de los siguientes comandos (veremos que significan en la siguiente sección).

```
cd $HOME
clear

```

<p>&nbsp;</p>


## 2. Directorios y su contenido
Cuando abrimos nuestra terminal Linux nos posiciona en un directorio definido por defecto, dicho directorio es llamado '_home_', y como puede imaginar, la ruta a un directorio por defecto varia segun la configuración de cada equipo de cómputo.

El comando `pwd` ('_print working directory_') nos indica exactamente en que directorio nos encontramos al momento. Verifique en su terminal en que ubicación se encuentra ahorita (ver Figura 1).


```
pwd
```

![Figura1](https://raw.githubusercontent.com/pclo/CLI/main/images/Diapositiva9.PNG)
Figura 1
<p>&nbsp;</p>

Cuando preparamos nuestra práctica descargamos y preparamos los archivos y directorios necesarios que requeriremos para realizar este tutorial. El directorio de la esta practica se llama _practical-cli_ y esta ubicando dentro de _home_. Trasladémonos a este directorio con la ayuda del comando `cd`

```
cd practica-cli
```
Note que hay un espacio entre el comando y el nombre del directorio.


¿Cuál es el contenido de este directorio? (consulte el contenido del directorio con el comando `ls`)
```
ls
```
¿Puede identificar dentro de todos estos nombres cuáles son archivos, directorios, programas o enlaces?. Más aún, ¿Puede decirnos más sobre el contenido de este directorio? Apoyese utilizando la opción `-l` del comando `ls` (ver Figura 2)
```
ls -l
```

![Figura2](https://raw.githubusercontent.com/pclo/CLI/main/images/Diapositiva10.PNG)
Figura 2
<p>&nbsp;</p>



¿Tiene la seguridad de que esta viento todo el contenido del directorio? 
Visualice los archivos escondidos en este directorio (de hecho, los archivos cuyos nombres inician con un punto '.') utilizando la opción `-a` del comando `ls` (ver Figura 2)
```
ls -la
```

Ahora traslademos entre directorios. Asegurese de que en este momento se estamos ubicados en el directorio _practical-cli_ (recuerde, `pwd`), puede ver parte del contenido de este directorio (y sus directorios internos) en la Figura 3.

![Figura3](https://raw.githubusercontent.com/pclo/CLI/main/images/Diapositiva11.PNG)
Figura 3

<p>&nbsp;</p>


Vaya al _dir1_ 
```
cd dir1
```

Despliegue el contenido de este directorio
```
ls
```

Regrese al directorio previo 
```
cd ..
```
Note que hay un espacio entre el comando `cd` y los dos puntos. Utilizamos los dos puntos para denotar “directorio previo”


Ahora vaya al _dir2_ 
```
cd dir2
```

¿Cómo despliego en mi ubicación actual el contenido del directorio previo?
```
ls ../
```

Ahora vaya al directorio _canasta_ 
```
cd canasta
```

Desde su ubicación actual, ¿cómo despliego el contenido del directorio _home_? 
```
ls ~/
```
O también puede utilizar:
```
ls $HOME
```

Regrese al directorio _dir2_ (que es el directorio previo con respecto a su ubicación actual) 
```
cd ..
```
<p>&nbsp;</p>

## 3. Remoción de archivos y directorios
¡Borremos algunas cosas! Recuerde que en este momento se supone que se usted se encuentra ubicado en el directorio _dir2_. Si este no es el caso, por favor trasladece a éste.

Elimine el archivo _borrame.txt_
```
rm borrame.txt
```
Ahora borre el directorio _estoy-aqui_
```
rm estoy_aqui
```
¿Qué sucedió? Linux no borro el directorio, necesitamos hacerle saber al sistema operativo que vamos a borrar un directorio, no un archivo, esto lo haremos añadiendo las opciones _-rf_ al comando _rm_
```
rm -rf estoy_aqui
```
<p>&nbsp;</p>


## 4. Cambo de nomvre de archivos y directorios
Podemos modificar el nombre de un archivo o directorio con ayuda del comando `mv`, que ahora utilizaremos para cambiar el nombre de un archivo y un directorio.

Vaya el diretorio _renombrar_, que se encuentra ubicado dentro del directorio _practica-cli_, después despliegue su contenido
```
cd ~/practica-cli/renombrar
ls
```

Cabie el nombre del archivo _carro.txt_ a _automobil.txt_ (verifique el cambio de nombre)
```
mv carro.txt automobil.txt
ls
```

Cambie el nombre del directorio _moto_ a _motorcicleta_ (Verifique el cambio)
```
mv moto motorcicleta
ls
```

Vaya de regreso al directorio _home_
```
cd ~/
```

<p>&nbsp;</p>


## 5. Compresión y descompresión
Existen varias opciones para realizar compresión y descompresión, veremos solo una de ellas por el momento. Usaremos el commando `tar` pata realizar estas tareas. 


Vaya al directorio _compresion-y-descompresion_  (que se encuentra dentro de _practical-cli_), verifique el contenidodel directorio, despuées descompirima el archivo _compreso.tar.gz_ y verifique de nuevo el contenido del directorio
```
cd ~/practica-cli/compresion-y-descompresion
ls
tar –xvzf compreso.tar.gz
ls
```

Comprima todos los archivos de texto y depositelos en un archivo llamado _nuevo.tar.gz_; verifique que se haya generado el archivo
```
tar –cvzf nuevo.tar.gz *.txt
ls
```

<p>&nbsp;</p>


## 6. Procesos
Visualicemos en nuestra Terminal todos los procesos que se estan realizando en este momento en nuestro equipo de cómputo. Esto lo haremos utilizando el comando `top` 

```
top
```
Presione `q` una vez que ya no quira salir de la visualización de procesos (ver Figura 4)

```
q
```
![Figura 4](https://raw.githubusercontent.com/pclo/CLI/main/images/Diapositiva12.PNG)
Figura 4

<p>&nbsp;</p>

Los procesos pueden ser visualizados e interrumpidos por medio de comandos como `pgrep`, `kill` o `pkill`, pero no los abordaremos en nuestro tutorial

<p>&nbsp;</p>


## 7. Crear y desplegar contenido
Desplacémonos al directorio _visualizar_ (ubicado dentro de _practica-cli_)
```
cd ~/practica-cli/visualizar/
```

Genere dos archivos utilizando el comando `touch`, a uno nómbrelo estrella.txt y al otro telescopio.txt 
Verifique que se hayan creado los archivos

```
touch estrella.txt
touch telescopio.txt
ls
```

Con ayuda del editor de texto `nano` añada al archivo _estrella.txt_ la letra 	de la canción 'El Pollito Pío'.
```
nano star.txt
```

Nota: Obtenga la letra de la canción de un navegador de internet. Siéntase en la libertad de copiar y pegar la letra en el editor de texto. 
Cuando tenga la letra seleccione y copie. Regrese al editor nano y presione el botón derecho del ratón, esto hará que se pegue lo que previamente copió

Una vez que termine de _ctrl+o_ para guardar los cambios y después  _ctrl+x_ para salir del editor.

<p>&nbsp;</p>

Ahora visualicemos el contenido de _telescopio.txt_ y de _estrella.txt_ con ayuda del comando _cat_
```
cat telescopio.txt
cat estrella.txt
```

¡Usted esta en lo correcto!Y, el archivo _telescopio.txt_ doesn't no contiene nada, por dicha razon no le mostró nada en pantalla. 
Por el lado contrario, el archivo _estrella.txt_ es muy extenso como para poder leerse correctamente en una sola visualización de pantalla. Recurramos a los comandos `head` y `tail` para ver unicamente el inicio y el fin de este archivo.
```
head estrella.txt
tail estrella.txt
```
<p>&nbsp;</p>

El comando `echo` nos ayuda a visualiza el contenido de variables (o de los argumentos de entrada). Recuerde que al inicio de la práctica lo utilizamos para visualizar los valores de algunas variables ambientales.

Existen varios editores de texto disponibles para Interfaces de Línea de Comando de sistemas Linux, por ejemplo `vi` y `pico`. En este tutorial solo hemos utilizado uno de ellos (`nano`).
<p>&nbsp;</p>

Muchas veces nos vemos en la necesidad de acceder a un archivo en diversas ubicaciones dentro de nuestro sistema de archivos. Una solución sería copiar el archivo y pegarlo en las ubicaciones que necesitamos, pero esto generaría el problema de estar duplicando múltiples veces un mismo archivo, y si este es de grán tamaño estaríamos desperdiciando espacio de disco. En estos casos recurrimos a lo que se le conoce como 'enlaces' y estos los generamos con ayuda del comando `ln`.

Trasladémonos a nuestro directorio _home_, creemos un enlace a nuestro archivo _estrella.txt_ y démosle el nombre _pollito_. (Recordemos que _estrella.txt_ se encuentra dentro del directorio visualizar)

```
cd ~/practica-cli
ln –s ./visualizar/estrella.txt pollito
cat pollito
```

Al visualizar el contenido de _pollito_ pudimos leer la letra de la canción (que en realidad esta contenida en _estrella.txt_).
<p>&nbsp;</p>

Regresemos al directorio _visualizar_
```
cd visualizar
```


<p>&nbsp;</p>


## 8. Análisis de texto
Limpie su pantalla y despliegue el contenido del directorio donde se encuentra en este momento (que debe de ser _visualizar_).
```
clear
ls
```
¡Extraigamos información de algunos archivos de texto! Utilizaremos los comandos `grep`, `wc`, `cut`, `sort` y `awk` (que es un lenguaje de programación por si mismo) para realizar estas tareas. 
 

¿Contiene el archivo cinco.txt la palabra “@mensaje”?
Utilicemos el comando `grep` para descrubrirlo.
```
grep @mensaje cinco.txt
```
¿En qué línea esta escrita la palabra"@mensaje" dentro del archivo _cinco.txt_?

```
grep -n @mensaje cinco.txt
```
<p>&nbsp;</p>

Contabilicemos cuantás veces aparece una palabra dentro de un archivo. 
¿Cuántas veces esta contenida la palabra “gato” dentro del archivo _diez.txt_?

```
grep -c gato diez.txt
```
<p>&nbsp;</p>

Ahora contabilicemos cuántas lineas contiene el archivo _transporte.txt_.
Utilizaremos el comando `wc` para obtener esta información.
```
wc -l transporte.txt
```

Despliegue el contenido del archivo _transporte.txt_. Observe que las palabras dentro de las oraciones estan separados por tabuladores (en lugar de espacios).
```
cat transporte.txt
```
¿Cómo visualizamos exclusivamente el contenido de la segunda columna del archivo _transporte.txt_?

Podemos realizar esta tarea utilizando dos distintos métodos. Podemos utilizar el comando `cut` o tambien podemos utilizar `awk`
```
cut -f2 transporte.txt
awk '{print $2}' transporte.txt
```
Por si mismo, `awk` es un lenguaje de programación. Es utilizado frecuentemente en análisis de texto, al igual que la programación Perl de línea única (Perl 'one-liners'). 

<p>&nbsp;</p>

Seamos un poco ordenados. Visualice el contenido de el archivo _clima.txt_
```
cat clima.txt
```
Este archivo contiene un listado de palabras, pero sin ningun orden. Utilicemos el comando `sort` para visualizar el contenido en orden alfabético de este archivo.

```
sort clima.txt
```

<p>&nbsp;</p>


## 9. Secuencias de procesos subsecuentes ‘pipelines’

En veces necesitamos combinar comandos y realizar un proceso después de otro. Hagamos tres secuencias de procesos subsecuentes, mejor conocidos como ‘pipelines’. Nos auxiliaremos de los símbolos  _|_ (pipe) y  _>_ (mayor que)
para realizar estas tareas.


Limpie su pantalla y despliegue el contenido del directorio en donde se encuenta en este momento (que debe de ser _visualizar_).

Utilicemos el símbolo _|_ (pipe) para poner en una sola línea todas las 	palabras que extrajimos de la segunda columna del archivo _transporte.txt_ 
```
cut -f2 transporte.txt|awk '{print}' ORS=' '
```

<p>&nbsp;</p>

Frecuentemente necesitamos guardar la salida de tareas que estamos realizando. Podemos hacer esto redireccionando la salida de nuestros procesos hacia algun archivo (que podemos visualizar posteriormente). Esto lo logramos auxiliandonos con el símbolo  _>_ (mayor que).

El símbolo _>_ permite redireccionar salidas (en este caso de pantalla). Vierta	las palabras resultantes de extraer la segunda columna del archivo 	_transporte.txt_ dentro de un nuevo archivo y llámelo _analisis.txt_. Después de esto despliegue el contenido de este nuevo archivo.

```
cut -f2 transporte.txt > analisis.txt
cat analisis.txt
```
<p>&nbsp;</p>

Finalmente, extraiga la tercera columna del archivo _final.txt_, ordénelo 	alfabéticamente, y guárdelo en un archivo llamado _teminamos.txt_
```
cut -f3 final.txt | sort > terminamos.txt
```

<p>&nbsp;</p>

## Un poco de trabajo adicional

Le dejo con un pequeño ejercicio extra. Extraiga la información de un archivo de anotación genuino (_Saccharomyces cerevisiae_, R64-1-1; en [formato GFT](http://m.ensembl.org/info/website/upload/gff.html)) proveniente de la base de datos de genomas [Ensembl](http://www.ensembl.org/Saccharomyces_cerevisiae/Info/Index).
 

<p>&nbsp;</p>

El [formato GTF](http://m.ensembl.org/info/website/upload/gff.html) contiene una ‘característica’ de secuencia (_feature_) por línea. Cada línea contiene 9 columna de datos, más líneas opcionales de definición de pista. 

Vamos a utilizar la anotación de genes de [_Saccharomyces cerevisiae_](http://www.ensembl.org/Saccharomyces_cerevisiae/Info/Index) y extraer información.


+ Abra su Interfaz de Líneas de Comandos y genere un directorio llamado _anotacion_: 
```
mkdir anotacion
```
+ Trasladece al directorio _anotacion_: 
```
mkdir anotacion
```

+ Descargue desde la [Plataforma FTP de Ensembl](http://ftp.ensembl.org/pub/release-104/gtf/saccharomyces_cerevisiae/) (R64-1-14) el archivo de anotación con el comando `wget`. Si tiene un sistema Mac no utilice `wget` utilice `curl`.
```
wget http://ftp.ensembl.org/pub/release-104/gtf/saccharomyces_cerevisiae/Saccharomyces_cerevisiae.R64-1-1.104.gtf.gz
```

**Para usuarios Mac 
```
curl http://ftp.ensembl.org/pub/release-104/gtf/saccharomyces_cerevisiae/Saccharomyces_cerevisiae.R64-1-1.104.gtf.gz -o Saccharomyces_cerevisiae.R64-1-1.104.gtf.gz 
```


+ Descomprima el archivo de anotación con el comando `gunzip`:  
```
gunzip Saccharomyces_cerevisiae.R64-1-1.104.gtf.gz 
```
+ Verifique que su archivo haya sido descomprimido (al visualizar el contenido de su directorio deberá de contener un archivo gtf en lugar de un archivo gtf.gz):    
```
ls
```
+ Ahora veamos las primeras 20 líneas del archivo:  
```
head -20 Saccharomyces_cerevisiae.R64-1-1.104.gtf
```
+ Las primeras 6 líneas del archivo no contienen ‘_features_’. Si queremos visualizar únicamente la porción del archivo que contiene los ‘_features_’ podemos auxiliarnos del comando `tail`. El archivo contiene demasiadas líneas como para poder ser fácilmente visualizado. Una solución es mandar exclusivamente el contenido de los ‘_features_’ a un archivo de texto. Hagamos esto y a este archivo llamémosle _solo-features.txt_ 
```
tail -n +6 Saccharomyces_cerevisiae.R64-1-1.104.gtf >solo-features.txt
```

+¿Cuántas líneas de ‘_features_’ están contenidas en este archivo de anotación?  (puede utilizar el comando `wc`) 
```
tail -n +6 Saccharomyces_cerevisiae.R64-1-1.104.gtf|wc -l
```
+ Observe el tipo de ‘_features_’ contenido en este conjunto de secuencias (en la columna 3):  
```
tail -n +6 Saccharomyces_cerevisiae.R64-1-1.104.gtf|cut -f3
```
+ Despliéguelos en orden alfabético:  (recuerde `sort`)
```
tail -n +6 Saccharomyces_cerevisiae.R64-1-1.104.gtf|cut -f3|sort
```
+ ¿Qué tipo de ‘_features_’ contiene la anotación? (puede utilizar el comando `uniq` para obtener un listado nombres sin repeticiones):   
```
tail -n +6 Saccharomyces_cerevisiae.R64-1-1.104.gtf|cut -f3|sort|uniq
```
+ ¿Cuántos _CDS_ contiene el archivo de anotación?:  
```
tail -n +6 Saccharomyces_cerevisiae.R64-1-1.104.gtf|cut -f3|grep -c CDS
```
+ ¿En qué números de línea del archivo de anotación podemos encontrar características tipo “_five_prime_utr_”?  
```
tail -n +6 Saccharomyces_cerevisiae.R64-1-1.104.gtf|cut -f3|grep -n five_prime_utr
```  


+ Si no quiere que aparezca “_five_prime_utr_” en el texto que se esta desplegando en pantalla puede eliminarlo con: 
```
tail -n +6 Saccharomyces_cerevisiae.R64-1-1.104.gtf|cut -f3|grep -n five_prime_utr|cut -f1 -d:
```
+ Podemos ver que tenemos cuatro ‘features’ tipo ”cd ” y están ubicados en la líneas 7297, 21190, 30433 and 38620

+ Utilice el editor `sed` para extraer la línea 7297
```
tail -n +6 Saccharomyces_cerevisiae.R64-1-1.104.gtf|sed -n '7297p’
```
+ Y podemos seguir, y seguir, y seguir…


