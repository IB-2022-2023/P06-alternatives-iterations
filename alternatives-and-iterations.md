# Práctica 06. Alternativas e Iteraciones

# Factor de ponderación: 6

### Objetivos
Los objetivos de esta práctica son que el alumnado:
* 

### Rúbrica de evaluacion de esta práctica
Se señalan a continuación los aspectos más relevantes (la lista no es exhaustiva) que se tendrán en cuenta a la hora de evaluar esta práctica:
* Se comprobará que el alumnado es capaz de escribir y evaluar expresiones que involucren diferentes tipos de
datos
* Ha de demostrar que conoce el proceso de compilación de programas usando el compilador de C++ de GNU
* Ha de acreditar que es capaz de subir programas a la plataforma 
[Jutge](https://jutge.org/)
para su evaluación
* Se comprobará que todos los ficheros (`*.cc`, `*.h`) de sus prácticas incluyen un comentario de cabecera
* Se comprobará que todos los programas de sus prácticas se ajusten a la
[Guía de estilo de Google para C++](https://google.github.io/styleguide/cppguide.html) 
* Ha de acreditar que es capaz de editar ficheros remotos en su VM usando vi
* Ha de demostrar que es capaz de ejecutar comandos Linux en su VM

### Github Classroom
En el futuro se utilizará GitHub Classroom (una plataforma relacionada con GitHub) para gestionar las
prácticas de *Informática Básica*.
En esa plataforma, para la realización de cada práctica recibirá una invitación a una tarea que tendrá que
aceptar.
Una vez acepte la invitación tendrá que clonar un repositorio asociado a la tarea.
Ese repositorio privado será el punto de partida y tendrá Ud. que añadir en él directorios con los programas
que realice.

El enlace de invitación a la tarea tiene una apariencia similar a
`https://classroom.github.com/a/uNbth9vD`.
Si lo introduce en un navegador, se le solicitará que se autentifique en su cuenta de GitHub.
Una vez autentificada/o le llevará a una pantalla
[como esta](https://raw.githubusercontent.com/IB-2022-2023/P06-alternatives-iterations/main/join-the-classroom-22-23.png?token=GHSAT0AAAAAAB2KIDMDGVFSGV5ZPKCEIPJQY2WOHQQ)
en la que se le solicitará que se una a la "classroom" IB-2022-2023.
Para ello ha de seleccionar su nombre de la lista de identificadores (*Identifiers*) que figura en esa página.
A continuación se le solicitará que "Acepte la tarea Practica-PRUEBAXXXXXXX" (habrá una tarea asociada con
cada una de las prácticas de la asignatura.

Cuando lo haya hecho aparecerá una pantalla 
[como esta](https://raw.githubusercontent.com/IB-2022-2023/P06-alternatives-iterations/main/accepted.png?token=GHSAT0AAAAAAB2KIDMCQ75PHT2TCKF2HUPSY2WOOPQ)
indicando que ha aceptado Ud. la tarea asignada
Cuando refresque la pantalla le mostrará 
[otra pantalla](https://raw.githubusercontent.com/IB-2022-2023/P06-alternatives-iterations/main/ready.png?token=GHSAT0AAAAAAB2KIDMDZNDJL6P5KDO3N4OEY2WOPIA)
en la que figura el enlace al repositorio que ha sido creado
para su trabajo en la práctica.

A través de ese enlace accederá Ud. en GitHub al repositorio privado que se ha creado para que desarrolle en
él los programas correspondientes a la práctica en cuestión.
[El enlace que figura en ese repositorio](https://raw.githubusercontent.com/IB-2022-2023/P06-alternatives-iterations/main/link.png?token=GHSAT0AAAAAAB2KIDMCQ4Z4HTEU2RJWWXDCY2WOQCA)
(elija la opción SSH para el enlace) es el que ha de entregar Ud. en la tarea del aula virtual correspondiente a la práctica.
Recuerde que tiene que entregar 2 elementos: este enlace a su repositorio y un fichero `.tar.gz` conteniendo
todos los programas que desarrolle tanto antes como durante la sesión de evaluación.
Ese enlace lo puede ya escribir en la tarea correspondiente del aula virtual: no es necesario que espere a la
sesión de evaluación para subirlo.
Sí ha de esperar a la sesión de evaluación para subir el fichero .tar.gz conteniendo sus programas.

Ese mismo enlace es el que ha de utilizar para realizar una copia local (clone) del repositorio en su máquina
virtual y comenzar a trabajar en los ejercicios de la práctica:

```
git clone https://github.com/IB-2022-2023/P06-alternatives-iterations <DirectorioLocal>
```

### La utilidad `make`
Hasta ahora en la asignatura se han compilado los programas que se desarrollan de forma manual, invocando al
compilador con un comando como
```
$ g++ -std=c++17 -Wall -o hello_world hello_world.cc
```
Tal como se ha explicado en las clases de teoría, por lo general, la compilación manual de programas es bastante tediosa, 
especialmente cuando el programa consta de varios ficheros con código fuente y es necesario especificar opciones 
adicionales del compilador.
En la práctica, lo más común es usar herramientas para automatizar el proceso de compilación, y `make` es una
de las herramientas mas usadas para tal propósito.

[make](https://en.wikipedia.org/wiki/Make_(software)) 
es una herramienta que permite automatizar el proceso de desarrollo de software.
La función de `make` es determinar automáticamente qué ficheros o módulos de un programa necesitan ser recompilados, 
y ejecutar los comandos necesarios para realizar esa tarea.

Estudie en las transparencias de clase 
[Make
utility](https://docs.google.com/presentation/d/1lYXrFHkka5VPkVukszQZq3VS9LNS5TOrA5m8fgkoQJQ/edit?usp=sharing)
los fundamentos de la utilidad.

Estudie asimismo el tutorial 
[A Simple Makefile Tutorial](https://cs.colby.edu/maxwell/courses/tutorials/maketutor/).
En ese tutorial se utiliza el compilador `gcc`, pero puede Ud. sustituirlo por `g++` puesto que el compilador
de C++ compila igualmente el código en C (como se ha explicado, C++ es un superconjunto de C).




### Ejercicios
1. Estudie el apartado 
[Conocer el código ASCII](http://www.minidosis.org/#/temas/Cpp.Expresiones)
(vídeo y ejemplos) del tutorial MiniDosis.

Tenga en cuenta que en MiniDosis se utiliza *la forma antigua* de realizar conversiones de tipos.
```cpp
int variable1;
double variable2 = 4.5;
variable1 = int(variable2);
```
En el código anterior en la sentencia `my_variable1 = int(my_variable2)` la segunda variable es *convertida* a
entero para asignar su valor a `variable1`.
Tal como se explica en
[Introduction to type conversion and
static_cast](https://www.learncpp.com/cpp-tutorial/introduction-to-type-conversion-and-static_cast/)
la forma más adecuada en C++ de realizar una conversión de tipos es usar el operador `static_cast`, de modo
que el código anterior sería equivalente a:
```cpp
int variable1;
double variable2 = 4.5;
variable1 = static_cast<int>(variable2);
```
Estudie el programa de ejemplo
[static_cast.cc](https://github.com/IB-2022-2023/IB-class-code-examples/blob/master/IntroductionToC%2B%2B/static_cast.cc)
de los utilizados junto a las transparencias de la asignatura.

Desinflado. Desarrolle un programa `desinflado.cc` que lea una letra mayúscula y muestre por pantalla su
correspondiente letra minúscula.

**Tests de funcionamiento**
```
Entrada Salida
   A      a
   M      m
```

2. Escriba un programa `boolean_operators.cc` que imprima en pantalla la
[tabla de verdad](https://en.wikipedia.org/wiki/Truth_table#Truth_table_for_all_binary_logical_operators)
de los operadores lógicos (and, or, not) de C++.
El programa deberá utilizar un par de variables booleanas y mostrar el resultado de operar ambas variables con
todos sus posibles valores y con cada uno de los operadores lógicos.

3. Escriba un programa `arithmetic_operators.cc` que declare e inicialice variables de tipos aritméticos e
imprima en pantalla el resultado de operar esas variables con todos los operadores que pueda utilizar con
ellas.
Utilice operadores aritméticos y de comparación.
El programa imprimirá en pantalla líneas como la siguiente:
```cpp
7 % 3 = 1
```
Para cada uno de los operadores considerados.

4. [C++ Tutor](http://pythontutor.com/cpp.html#mode=edit) es una herramienta que a través de una interfaz web
permite "visualizar" la ejecución de programas escritos en C++ (también tiene soporte para otros lenguajes).
Experimente con la herramienta y ejecute con ella los programas que haya estudiado en clase, así como todos
los programas correspondientes a los ejercicios anteriores.
Al usar la herramienta, preste especial atención a la ejecución del programa `references.cc`

5.- Escriba un programa que solucione el problema 

[P48107](https://jutge.org/problems/P48107) Integer division and remainder of two natural numbers

y evalúe su solución utilizando Jutge.
Recuerde que Jutge solo evalúa la corrección de su programa desde un punto de vista del funcionamiento.
Su código ha de cumplir adicionalmente con los requisitos de formato y estilo.
