# ABAP

## Reglas básicas

El formato básico de las reglas ABAP es simple:

-   Cada declaración ABAP debe terminar en un punto
-   Los elementos dentro de cada declaración deben estar separados al menos por un espacio
-   El final de línea es equivalente al espacio
-   Las declaraciones y palabras clave **no** distinguen entre mayúsculas y minúsculas
## Tipo de datos
|TIPO|DESCRIPCION  |
|--|--|
|  I|Entero (4-bytes)  |
|P|decimal|
|F|Punto Flotante
|N|Caracter numérico
|C|Caracter
|D|Fecha
|T|Tiempo
|X|Hexadecimal
|STRING | Cadena de caracteres
|XSTRING|Variable-length raw byte array

## Declaración de variables y constantes
**DATA** nombre_variable **TYPE** I.
**DATA** nombre_variable2 **TYPE** I **VALUE** 10.
**CONSTANTS** nombre_constante **TYPE** I **VALUE** 123.

