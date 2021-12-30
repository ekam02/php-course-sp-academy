# PHP

## ¿Qué es PHP?

Es un lenguaje de programación de alto nivel e interpretado; de tipado débil,
por lo que no es necesario definir el tipo de dato al momento de la declaración
y/o asignación ya que el intérprete se encargará de esta tarea durante la
ejecución del programa. Sus siglas *PHP* representan el acrónimo recursivo
*PHP: Hypertext Preprocessor*.

## Instalación en Windows

La manera más fácil de instalar PHP es mediante la instalación del paquete
_XAMPP_ desde la [web oficial](https://www.apachefriends.org/es/index.html).

### *Instalación manual*

Para lograr la instalación del interprete en windows, descargue la utilidad
_Visual C++ Redistributable_ <small>(vc_redist)</small> de Microsoft,
correspondientes a la arquitectura del sistema operativo, desde la
[página oficial](https://docs.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170).

<img src="./img/vcredist 2021-12-28_155010.png" alt="Página oficial del proyecto vc_redist." />

Instale la utilidad `vc_redist` en el equipo.

<img src="./img/vcredist 2021-12-28_155141.png" alt="Instalación de la utilidad vc_redist." />

<img src="./img/vcredist 2021-12-28_155149.png" alt="Instalación de la utilidad vc_redist." />

Es posible que requiera reiniciar el equipo.

<img src="./img/vcredist 2021-12-28_155231.png" alt="Solicitud de reinicio." />

Descargue los binarios del proyecto PHP, correspondientes a la arquitectura del
sistema operativo, desde la [página oficial](https://www.php.net/downloads.php).

<img src="./img/Instalación de PHP 2021-12-28_151735.png" alt="Página oficial del proyecto PHP." />

<img src="./img/Instalación de PHP 2021-12-28_151922.png" alt="Selección de binarios para arquitectura x64." />

Descomprima los binarios en un directorio que se ubique en el disco principal
donde está alojado el sistema operativo; para este caso se trata del disco
local `C:`.

<img src="./img/Instalación de PHP 2021-12-28_152048.png" alt="Directorio ubicado en el disco principal." />

Agregue la ruta en la variable de entorno `Path` del sistema operativo.

<img src="./img/Instalación de PHP 2021-12-28_152229.png" alt="Propiedades del sistema." />

<img src="./img/Instalación de PHP 2021-12-28_152325.png" alt="Variables de entorno." />

<img src="./img/Instalación de PHP 2021-12-28_152416.png" alt="Editor variable PATH." />

Compruebe que el sistema reconoce el interprete de PHP con el comando `php -v`
o `php --version`.

<img src="./img/Instalación de PHP 2021-12-28_160449.png" alt="Editor variable PATH." />

## Instalación en Ubuntu

Para instalar versiones más reciente de PHP en una distribución Linux (Ubuntu)
se recomienda agregar el repositorio al administrador de paquetes. Para esto
escriba el siguiente comando en su terminal.

``` bash
sudo add-apt-repository ppa:ondrej/php
```

Luego, será necesario actualizar los repositorios del sistema con el siguiente
comando.

``` bash
sudo apt update
```

Opcionalmente, actualice las herramientas del sistema con el siguiente comando.

``` bash
sudo apt upgrade
```

Para instalar el intérprete lance el siguiente comando `sudo apt install php`
sobre la terminal; es posible especificar la versión del interprete agregándola
luego del argumento `php` por ejemplo:

``` bash
sudo apt install php8.0
```

``` bash
sudo apt install php7.1
```

El servidor HTTP *Apache* puede requerir para la interpretación correcta de los
documentos PHP la librería `libapache2-mod-php`. Para instalarla use el
siguiente comando:

``` bash
sudo apt install libapache2-mod-php8.0
```

### *Configuración Apache <sup><small>\[OPCIONAL\]\[LINUX\]</small></sup>*

El servidor http *Apache* solo puede estar asociado un interprete de PHP; por
lo que es necesario habilitar y deshabilitar los interpretes según la
necesidad. Para deshabilitar una versión use el comando `sudo a2dismod php8.0`.
Para habilitar una versión use el comando `sudo a2enmod php8.0`. Una vez
aplicados los cambios será necesario reiniciar el servicio de Apache, usando el
comando `sudo systemctl restart apache2`.

## Consola interactiva

Para ingresar a la consola interactiva, proporcionada por el programa, use el
siguiente comando en la terminal de Linux o en la consola de Windows.

``` bash
php -a
```

<img src="./img/PHP -a 2021-12-29_192317.png" alt="Ingreso a la consola interactiva." />

## Creando documentos PHP válidos

Use un editor de texto plano de su preferencia para crear un nuevo documento
PHP válido; tenga en cuenta que todo documento deberá iniciar con el prefijo
(apertura de bloque) `<?php`. A menos que esté trabajando sobre documentos HTML
deberá finalizar la sección correspondiente a PHP con el sufijo (cierre de
bloque) `?>`.

Cree un documento php con el nombre `index.php` y guarde el siguiente bloque de
código en su interior; para mostrar información del intérprete PHP desde un
navegador. Por convención lo servidores web esperan interpretar un archivo
nombrado *«index»*.

``` php
<?php
phpinfo();
```

Si está usando el sistema operativo Windows con XAMPP ubique el archivo en la
ruta `C:\xampp\htdocs\`; si por el contrario está usando una distribución Linux
ubique el archivo en la ruta `/var/www/html/`. Para ambos casos abra un
navegador y escriba en la barra de navegación la siguiente URL
`http://localhost`. Si usa WSL use el comando `sudo /etc/init.d/apache2 start`
para iniciar el servidor de Apache.

<img src="./img/localhost 2021-12-29_201225.png" alt="Ingreso a la consola interactiva." />

## Habilitando Errores *<sup><small>\[LINUX\]</small></sup>

Por defecto el interprete de PHP no muestra errores; para mostrarlos se busca
el atributo `display_errors` del archivo `php.ini` en el directorio
`/etc/php/8.0/apache2/`; cambiando el valor `Off` por `On`.


## Ejecutando código PHP por consola

Para lograr ejecutar código PHP escrito dentro de un archivo use el comando
`php` y entregue el archivo como argumento de entrada para el proceso.

``` bash
php suma.php
```

## Sintaxis PHP

Antes de continuar tenga presente que gran parte de las instrucciones en PHP
terminan o se cierra con el caracter `;`. Las comillas dobles y sencillas tiene
comportamientos diferentes sobre el texto; tal que las comillas dobles sirven
para simplificar el proceso de concatenar texto, pudiendo agregar variables
dentro del mismo teniendo la posibilidad que el intérprete de PHP reemplace el
identificador por el valor guardado por la variable; mientras que las comillas
simples no entrega esa posibilidad, imprimiendo el identificador como un texto
más.

Para concatenar texto y operaciones use el caracter `.`

### `echo`

Es la función que ayuda a imprimir en la terminal el texto o el resultado de
alguna operación entregada.

``` terminal
php > echo "¡Hola Mundo!";
¡Hola Mundo!
php >
```

Tenga en cuenta que la función `echo` no termina con saltos de líneas, por lo
que deberá agregarlas; para agregarla es necesario escribir `\n` cuando se
trata de texto impreso por terminal o sobre un archivo de texto plano, o la
etiqueta de salto de línea `<br/>` para imprimir documentos HTML.

## Constantes y Variables

Las variables y las constantes son estructuras que guardan valores necesarios
para el funcionamiento del programa.

Sin embargo, las variables se declaran anteponiendo el signo `$` (peso o dólar)
al nombre de estas, y se inicializan entregando un valor luego de poner el
operador de asignación `=`.

``` PHP
$variable_1 = 99;
$variable_2 = 15;
echo $variable_1 + $variable_2;  // int(114)
```

Las variables pueden cambiar su valor durante el tiempo de ejecución del
programa. Por ejemplo, pasando de guardar un número a guardar una cadena de
caracteres.

``` PHP
$variable_3 = 50;
echo $variable_3;  // int(50)
$variable_3 = "Andrés";
echo $variable_3;  // string(6) "Andrés"
```

Las constantes se declaran con la función `define()`; esta función recibe por
argumento dos valores separados por una coma (`,`), siendo el primero el nombre
de la constante encerrado entre comillas dobles, y el segundo, el valor de
esta. Por convención se espera que el nombre sea en mayúsculas.

``` PHP
define("NUMERO_E", 2.7183);
echo NUMERO_E;  // float(2.7183)
```

Para usar las constantes, no hay necesidad de anteponer el signo `$`.

## Tipos de datos

Los _tipos de datos_ se puede interpretar como etiquetas o denominaciones
entregadas a conjuntos de datos distinguibles. Por ejemplo, el superconjunto de
los números, el superconjunto de los caracteres, el conjunto de los valores
vacíos.

Entre los tipos de datos más conocidos en el mundo de la programación se
tienen:

- Numéricos
  - Integer *(enteros)*
  - Float *(reales)*
  - Double *(reales con precisión)*
- Cadenas de caracteres
  - Char *(letra o símbolo)*
  - String *(cadena de caracteres)*
- Booleanos
  - Bool *(usados en la álgebra de Boole)*
- Sin valor
  - Null *(sin valor)*
  - Undefined *(sin inicialización)*

Al ser PHP un lenguaje de programación de *tipado débil* el intérprete se
encargará de inferir en tiempo de ejecución el tipo de valor asignado a una
variable. Asi mismo, PHP es capaz de convertir un tipo de dato a otro, si el
nuevo valor asignado es de un tipo diferente al entregado inicialmente, o
dependiendo el contexto. Si se intenta realizar una operación matemática entre
un número guardado como _String_ y otro siendo un _Float_; el primer valor
String será convertido en un tipo Float para lograr completar la operación.

A continuación, se muestra un ejemplo de lo mencionado:

``` php
$var_1 = "50";  // string(2) "50"
$var_2 = 44;  // int(44)
$var_3 = $var_1 + $var_2  // int(94)
```

## Casting

El _Casting_ es la manera de indicar al interprete de PHP para forzar el cambio
de un tipo de dato a otro deseado. Se puede acceder a esta utilidad
anteponiendo el *tipo de dato* entre paréntesis antes de un valor o una
variable al momento de la asignación o inicialización.

Las siguientes definiciones ayudan a forzar el cambio de tipos en PHP:

|     Casting | *Efecto*                           |
|------------:|:-----------------------------------|
|   `(array)` | *Fuerza al tipo arreglo*           |
|    `(bool)` | *Fuerza al tipo booleano*          |
| `(boolean)` | *Fuerza al tipo booleano*          |
|  `(double)` | *Fuerza al tipo 'punto flotante'*  |
|   `(float)` | *Fuerza al tipo 'punto flotante'*  |
|     `(int)` | *Fuerza al tipo entero*            |
| `(integer)` | *Fuerza al tipo entero*            |
|  `(object)` | *Fuerza al tipo objeto*            |
|  `(string)` | *Fuerza al tipo 'cadena de texto'* |

A continuación, se muestra un par de ejemplos de lo mencionado:

``` php
$var_3 = "5";  // string(1) "5"
$var_4 = (int) $var_3;  // int(5)
```

``` php
$flag = 1;  // int(1)
$flag = (bool) $flag;  // bool(true)
```

## Operadores lógicos

Los *Operadores Lógicos* son elementos usados para la evaluación de
*Expresiones*, confirmando si estas son verdaderas o falsas. Una Expresión
consta de al menos dos *Afirmaciones*, como podría ser *«Los seres humanos no
pueden vivir sin oxígeno»* o *«One-Punch Man tiene una frondosa cabellera»*.
Una *Afirmación* no es mas que una oración que puede contener una verdad o una
falsedad.

La evaluación de expresiones se pueden reducir a las *tablas de verdad*; las
cuales operan sobre expresiones de dos afirmaciones. PHP usa los operadores
`and` y `or` para las tablas de verdad $y$ y $o$ respectivamente.

### *Tabla de verdad $y$ (`and`)*

Use el operador `and` para comprobar, sí ambas afirmaciones en una expresión
son verdad toda la expresión es verdad, pero sí una de las afirmaciones es
falsa toda la expresión es falsa.

| Valor   | Operador | Valor   | Resultado |
|:-------:|:--------:|:-------:|:---------:|
| `true`  | `and`    | `true`  | `true`    |
| `true`  | `and`    | `false` | `false`   |
| `false` | `and`    | `true`  | `false`   |
| `false` | `and`    | `false` | `false`   |

### *Tabla de verdad $o$ (`or`)*

Use el operador `or` para comprobar, sí al menos una de las afirmaciones en una
expresión es verdad toda la expresión es verdad, pero sí ambas afirmaciones son
falsas toda la expresión es falsa.

| Valor   | Operador | Valor   | Resultado |
|:-------:|:--------:|:-------:|:---------:|
| `true`  | `or`     | `true`  | `true`    |
| `true`  | `or`     | `false` | `true`    |
| `false` | `or`     | `true`  | `true`    |
| `false` | `or`     | `false` | `false`   |

PHP también soporta los operadores `&&` y `||` para las evaluaciones $y$ y $o$
respectivamente.

### *Tabla de verdad $y$ (`&&`)*

| Valor   | Operador | Valor   | Resultado |
|:-------:|:--------:|:-------:|:---------:|
| `true`  | `&&`     | `true`  | `true`    |
| `true`  | `&&`     | `false` | `false`   |
| `false` | `&&`     | `true`  | `false`   |
| `false` | `&&`     | `false` | `false`   |

### *Tabla de verdad $o$ (`||`)*

| Valor   | Operador | Valor   | Resultado |
|:-------:|:--------:|:-------:|:---------:|
| `true`  | `\|\|`   | `true`  | `true`    |
| `true`  | `\|\|`   | `false` | `true`    |
| `false` | `\|\|`   | `true`  | `true`    |
| `false` | `\|\|`   | `false` | `false`   |

### *Operador de negación (`not`)*

Para negar o invertir el valor de una afirmación se usa el operador $no$ (`!`).

| Operador | Valor   | Resultado |
|:--------:|:-------:|:---------:|
| `!`      | `true`  | `false`   |
| `!`      | `false` | `true`    |
