# ABAP - Ejercicios

## (1) Hola mundo
Hola mundo en ABAP

    REPORT  Z_EDWINSPIRE_01.
    WRITE: /'Hola mundo ABAP'.


## (2) Declaracion de variables y Constantes
Las variables se declaran con **DATA** en nombre de la variable, tipo y opcionalmente el valor de fábrica.
De forma similar las constantes se declaran usando la palabra reservada **CONSTANTS**, a diferencia de la declaracion de variables, para las constantes el valor es obligatorio.

    REPORT  Z_EDWINSPIRE_02.

    * Declaración de variables una por linea. 
    DATA var1 TYPE I.
    DATA var2 TYPE I VALUE 10.
    CONSTANTS const1 TYPE STRING VALUE 'ABAP'.
    * Declaración de variables en una solo linea
    DATA: var3 TYPE STRING VALUE 'Hola', var4 TYPE STRING.
    * Asignamos los valores a las variables
     var1 = 123. 
     var4 = 'Mundo'.
    WRITE: /'var1 = ',var1.
    WRITE: /'var2 = ',var2.
    WRITE: /'Valor de la constante = ',const1. "Aqui se imprime el valor de la constante
    WRITE: /'', var3,' ',var4.
    var4 = 'Asignación de valor a la variable con un texto' &
    ' largo en mas de una linea.'.
    WRITE: /'var4 = ',var4.
    * Podemos usar tambien MOVE para asignar los valores de una variable a otra
    MOVE var3 TO var4.
    WRITE: /'var4 = ',var4.

## (3) Parámetros de entrada
En este ejemplo se mostrará en pantalla un cuadro de texto para que el usuario pueda ingresar un dato que se imprimirá en pantalla.

    REPORT  Z_EDWINSPIRE_03.
    PARAMETERS dato1 TYPE string.
    WRITE dato1.

## (4) Variables del sistema
Imprime en pantalla algunas de las variables del sistema: 

    REPORT  Z_EDWINSPIRE_04.
    WRITE: /'Fecha local del usuario: ', SY-DATLO.
    WRITE: /'Hora local del usuario: ', SY-TIMLO. 
    WRITE: /'Valor devuelto por el último comando: ', SY-SUBRC.
    WRITE: /'Nombre de la actual transacción: ',  SY-TCODE.
    WRITE: /'Nombre del usuario actual: ', SY-UNAME.
    WRITE: /'Nombre del actual programa ABAP: ', SY-REPID.

## (5) Operaciones con cadenas
Operaciones básicas con cadenas:

    REPORT  Z_EDWINSPIRE_05.
    WRITE: /'Hola mundo ABAP'.