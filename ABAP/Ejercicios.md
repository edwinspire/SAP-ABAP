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
    DATA Contador TYPE I VALUE 0.
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
    DO 8 TIMES.
      Contador = Contador + 1.
      " SY-INDEX guarda el contador del LOOP
      IF SY-INDEX = 5.
      WRITE: /'SY-INDEX ES = 5'.
     ELSE.
      WRITE: /'SY-INDEX ES:', SY-INDEX. "Es el indice del Loop actual.
      ENDIF.
    ENDDO.

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
    PARAMETERS texto1 TYPE string.
    DATA: var1 TYPE string VALUE ' Una cadena.', var2 TYPE string, longitud TYPE i VALUE 0.

    WRITE: /'PARAMETRO DE ENTRADA: ', texto1.

    WRITE: /'STRLEN:', /'Obtiene la longitud de una cadena:'.
    longitud = strlen( texto1 ).
    WRITE: /'', longitud, ' caracteres'.

    WRITE: /'CONCATENATE:', /'Concadenar el parametro de entrada                            con var1:'.
    CONCATENATE texto1 var1 INTO var2 SEPARATED BY  '>'.
    WRITE: /'',var2.

    WRITE: /'CONDENSE:', /'Elimina todos los espacios en blanco al comienzo y al final de la cadena:'.
    MOVE texto1 TO var1.
    CONDENSE var1.
    WRITE: /'',var1.

    WRITE: /'REPLACE:', /'Reemplaza la primera aparición de A por X en la cadena pasada como parámetro:'.
    var1 = texto1.
    REPLACE 'A' WITH 'X' INTO var1.
    WRITE: /'',var1.

    WRITE: /'SEARCH:', /'Busca una cadena (hola) dentro de otra (texto1) y guarda el resultado en la variable del sistema SY-SUBRC (0 si es encontrada, 4 en caso contrario):'.
    var1 = texto1.
    SEARCH texto1 FOR 'hola' ABBREVIATED.
    WRITE: /'', sy-subrc.

    WRITE: /'SHIFT:', /'Elimina los primeros caracteres de una cadena (5 para este ejemplo):'.
    var1 = texto1.
    SHIFT var1 BY 3 PLACES.
    WRITE: /'', var1.
    
    WRITE: /'SPLIT:', /'Divide una cadena segun el caracter asignado:'.
    SPLIT texto1 AT ',' INTO var1 var2.
    WRITE: /'', var1, var2.


    WRITE: /'TRASLATE:', /'Convierte texto a mayusculas o minusculas:'.
    var1 = texto1.
    TRANSLATE var1 TO LOWER CASE.
    WRITE: /'', var1.
    
    
## (6) sy-vline  Líneas tipo tabla
**sy-vline** permite crear columnas para delimitar el contenido de un reporte, simulando una tabla.

    REPORT  Z_EDWINSPIRE_06.
    PARAMETERS: nombre TYPE STRING.
    DATA index TYPE I VALUE 0.

    WHILE index < 10.
    WRITE: /'',index, sy-vline,
    nombre, sy-vline.
    index = index + 1.
    ENDWHILE.

## (7) Operaciones matemáticas
**sy-vline** permite crear columnas para delimitar el contenido de un reporte, simulando una tabla.

    REPORT  Z_EDWINSPIRE_07.
    PARAMETERS: numero TYPE I.
    DATA: A TYPE F VALUE 100.
    DATA: R TYPE F.

    WRITE: /'Su número: ',numero.

    R = numero + 100. WRITE: /'Suma: ',numero,' + 100 = ',R.
    A = R - 78. WRITE :  /'Resta: ',R,' - 78 = ',A.
    A = R / 2. WRITE : /'División: ',R,' / 2 = ',A.
    A = R * 25. WRITE : /'Multiplicación: ',R,' * 25 = ',A.
    A = R DIV 3. WRITE : /'División entera: ',R,' / 3 = ',A.
    A = SIN( R ). WRITE : /'Seno de ',R,' = ',A.
    A = COS( R ). WRITE :  /'Coseno de ',R,' = ',A.
    A = SQRT( R ). WRITE : /'Raíz cuadrada de ',R,' = ',A.
    A = LOG( R ). WRITE : /'Logaritmo neperiano de ',R,' = ',A.
    A = LOG10( R ). WRITE : /'Logaritmo base 10 de ',R,' = ',A.

    WRITE: /'*** REDONDEOS ***'.
    R = A * -1.
    A = ABS( R ). WRITE : /'ABS(',R,') = ',A.
    A = SIGN( R ). WRITE : /'SIGN(',R,') = ',A.
    A = CEIL( R ). WRITE : /'CECIL(',R,') = ',A.
    A = FLOOR( R ). WRITE : /'FLOOR(',R,') = ',A.
    A = TRUNC( R ). WRITE : /'TRUNC(',R,') = ',A.
    A = FRAC( R ). WRITE : /'FRAC(',R,') = ',A.

## (8) CHECK
La instrucción CHECK evalua una condición, si es falsa todo el resto de instrucciones dentro de un LOOP son ignoradas.

    REPORT  Z_EDWINSPIRE_08.
    DO 5 TIMES.
    CHECK SY-INDEX BETWEEN 3 AND 4.
    Write / SY-INDEX.
    ENDDO.'.


## (9) IF ELSEIF ENDIF
La instrucción CHECK evalua una condición, si es falsa todo el resto de             instrucciones dentro de un LOOP son ignoradas.

    REPORT  z_edwinspire_09.
    PARAMETERS: nombre TYPE string.
    DATA resultado TYPE string.

    IF strlen( nombre ) EQ 0.
      resultado = 'Debe ingresar un nombre'.
    ELSEIF strlen( nombre ) > 5.
      resultado = 'Su nombre no puede tener mas de 5 caracteres'.
    ELSE.
      CONCATENATE 'Su nombre es' nombre INTO resultado.
    ENDIF.

    WRITE resultado.

