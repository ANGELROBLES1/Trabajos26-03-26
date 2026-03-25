# Trabajos26-03-26

### Arbol de Sintaxis con Gramatica Libre de Contexto

Requerimientos

1. Archivos necesarios

El programa requiere los siguientes archivos ubicados en la misma carpeta:

parser_arbol.py  
entrada.txt  

El archivo entrada.txt debe contener dos partes:

Primera parte  
La gramatica definida mediante reglas de produccion  

Segunda parte  
La cadena a evaluar  

Ambas partes deben estar separadas por el simbolo:

%%

Ejemplo de contenido de entrada.txt:

E -> T Ep  
Ep -> + T Ep | epsilon  
T -> F Tp  
Tp -> * F Tp | epsilon  
F -> id  

%%  
id + id * id  

Cada linea antes de %% representa una regla de la gramatica  
La linea despues de %% representa la cadena que sera analizada  


2. Abrir la terminal

Abrir una terminal en el sistema operativo Ubuntu  
Se puede usar el atajo:

Ctrl + Alt + T  


3. Navegar hasta la carpeta del programa

Usar comandos para ubicarse en el directorio donde estan los archivos  

Ejemplo:

cd ~/Escritorio  

Para verificar los archivos:

ls  

Deben aparecer:

parser_arbol.py  
entrada.txt  


4. Ejecutar el programa

Una vez ubicado en la carpeta correcta, ejecutar el siguiente comando:

python3 parser_arbol.py  

El programa lee automaticamente el archivo entrada.txt  
No es necesario pasar el archivo como parametro  


5. Funcionamiento del programa

El programa realiza los siguientes pasos:

Lee el archivo entrada.txt  

Separa la gramatica y la cadena usando el simbolo %%  

Construye internamente una estructura de la gramatica  
donde cada no terminal tiene sus producciones  

Divide la cadena en tokens individuales  

Inicia el analisis sintactico desde el simbolo inicial  
que corresponde a la primera regla de la gramatica  

Aplica un metodo recursivo con backtracking  
probando cada produccion posible hasta encontrar una derivacion valida  

Si logra derivar completamente la cadena  
construye el arbol de sintaxis  


6. Salida del programa

El programa muestra el resultado en consola  

Caso correcto:

Arbol de sintaxis generado  

seguido de la estructura jerarquica del arbol  


Caso con errores:

El programa imprime un mensaje de error indicando el problema  

Ejemplos de errores posibles:

Error sintactico se esperaba un token diferente  
Error simbolo no definido en la gramatica  
Error en formato del archivo  
Error falta separador %%  
Error tokens sobrantes  


Esto permite identificar en que parte falla la gramatica o la cadena  


7. Interpretacion del resultado

El arbol de sintaxis representa como la cadena es generada  
a partir de la gramatica  

Cada nodo corresponde a un simbolo  
y sus hijos representan la produccion aplicada  

Si el arbol se genera correctamente  
significa que la cadena pertenece al lenguaje definido  

Si ocurre un error  
significa que la cadena no puede ser generada por la gramatica  


8. Consideraciones

El programa funciona con gramatica libre de contexto  

Utiliza backtracking por lo que puede probar multiples caminos  

No esta optimizado para gramaticas ambiguas  

Es adecuado para pruebas academicas y validacion de cadenas  


9. Objetivo del programa

El objetivo es simular el proceso de analisis sintactico  
y construir el arbol que representa la derivacion de una cadena  

Esto permite entender como un compilador interpreta estructuras  
a partir de reglas formales  
