# Respuestas a Compilador

# INTRODUCCION #
 
El archivo `calculator.c` es un programa sencillo, que suma
dos números y los imprime en pantalla; así y todo compilarlo 
requiere un montón de pasos intermedios. Estos pasos los podemos 
clasificar en 4:

1. Pre-procesador: `make preprocessing`
2. Compilacion I: `make assembler`
3. Compilacion II: `make object`
4. Linkeo: `make executable`

Ejecutando cada una de las instrucciones de `make` van a poder
construir cada uno de los pasos intermedios.

1. Escriban qué esperan de cada uno de los pasos

En la primera etapa, el del Pre-procesador se encarga de las directivas # como los includes y las macros. En este caso, incluye 
<stdio.h> y, a su vez, todos los que éste incluya, como ser la funcion `printf`. Incluye al header `calculator.h` y luego el contenido de `calculator.c`. Luego de este paso ya estan declaradas todas las funciones que luego se usan en el codigo. El segundo paso, llamado Compilacion I se encarga de transformar el codigo de C a `assembler`, en este paso se ponen los argumentos y se llaman a las funciones que se usan en el codigo como ser:

	call	add_numbers

	call	printf

En el paso de Compilacion II pasamos de assembler a lenguaje de maquina. En este paso se generan los objetos en binario y aparece cierta informacion respecto de las caracteristicas de las funciones que se llaman en el codigo

000000000000003c T add_numbers
0000000000000000 T main
                 U printf

En este caso las funciones add_numbers y main son tipo texto y las mayusculas indican que se pueden linkear de manera externa.

Finalmente llega el paso de linkeo donde se genera el ejecutable y se `linkea` a las librerias para definir las funciones.

2. ¿Qué agregó el preprocesador?

El preprocesador agrega todas las declaraciones en las librerias que se llaman en el codigo, como ser `<stdio.h>` y `calculator.h`.

3. Identificar en la rutina de assembler las funciones

	call	add_numbers

	call	printf

4. Explicar qué quieren decir los símbolos que se crean en el objeto

000000000000003c T add_numbers
0000000000000000 T main
                 U printf

T text
U undefined
R read only
D data

minusculas: no se puede linkear desde afuera
mayusculas: si se puede linkear desde afuera

recien en el proceso de linkeo, al final en donde se genera el ejecutable es cuando linkea con las librerias y define las funciones como `printf`

5. ¿En qué se diferencian los símbolos del objeto y del ejecutable?

En el ejecutable se agregan otros simbolos y ademas los que ya estaban aparecen linkeados, es decir, ya le dice en que direccion tiene que buscarlos como ser el caso del `printf`

U printf@@GLIBC_2.2.5


