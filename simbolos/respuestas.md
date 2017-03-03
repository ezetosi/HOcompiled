# Respuestas a Símbolos 
 
El archivo `visibility.c` tiene muchos tipos de símbolos. En
este trabajo sólo tienen que compilar el objeto `visibility.o` 
e identificar los símbolos, ejecutando:

```
make object
```

Simbolos que aparecen al correr `make object`

0000000000000000 t add_abs
000000000000002a T main
                 U printf
0000000000000000 r val1
0000000000000004 R val2
0000000000000000 d val3
0000000000000004 D val4

efectivamente aparece todo tipo de simbolo:
T -> text
U -> undefined
R -> read only
D -> data

algunos estan en mayusculas y otros en minusculas, los que estan en mayuscula se pueden linkear de manera externa, mientras que los otros no, por ejemplo veamos la variable `val1`

`static const int val1 = -5;`

al estar definida como `static` no puede modificarse externamente, por eso el simbolo aparece en minusculas.
