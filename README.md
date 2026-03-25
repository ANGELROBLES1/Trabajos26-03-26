
# Arbol de Sintaxis con Gramatica Libre de Contexto

# Requerimientos

# 1. Archivos necesarios

El programa requiere los siguientes archivos ubicados en la misma carpeta:

- punto1.py  
- entrada.txt  

El archivo entrada.txt debe contener dos partes:

- Primera parte:
La gramatica definida mediante reglas de produccion  
- Segunda parte: 
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


# 2. Abrir la terminal
# 3. Navegar hasta la carpeta del programa
Deben aparecer:

punto1.py  
entrada.txt  
# 4. Ejecutar el programa

- python3 parser_arbol.py  

# 5. Funcionamiento del programa

El programa realiza los siguientes pasos:

Lee el archivo entrada.txt  

Separa la gramatica y la cadena usando el simbolo %%  

Construye internamente una estructura de la gramatica donde cada no terminal tiene sus producciones. Divide la cadena en tokens individuales. Inicia el analisis sintactico desde el simbolo inicial que corresponde a la primera regla de la gramatica  

Aplica un metodo recursivo probando cada produccion posible hasta encontrar una derivacion valida  


# 6. Interpretacion del resultado

El arbol de sintaxis representa como la cadena es generada a partir de la gramatica. Cada nodo corresponde a un simbolo y sus hijos representan la produccion aplicada  
Si el arbol se genera correctamente significa que la cadena pertenece al lenguaje definido  
Si ocurre un error significa que la cadena no puede ser generada por la gramatica  
Esto permite entender como un compilador interpreta estructuras a partir de reglas formales  
<img width="446" height="404" alt="image" src="https://github.com/user-attachments/assets/134595e1-47bc-451a-a20b-493357892801" />

El nodo raiz es E, que corresponde al simbolo inicial de la gramatica. Desde este nodo se deriva toda la expresion.

La produccion aplicada es:

E -> T Ep  

Esto divide la expresion en dos partes:

- T representa el primer operando  
- Ep representa el resto de la expresion  

## 1. El primer T se deriva como:

T -> F Tp  
F -> id  

Esto representa el primer valor de la expresion:

id  

## 2. Luego Ep se deriva como:

Ep -> + T Ep  

Aqui aparece el operador +, indicando que la expresion continua.

## 3. El segundo T se deriva como:

T -> F Tp  
F -> id  

Pero adicionalmente:

Tp -> * F Tp  
F -> id  

Esto representa la operacion:

id * id  

## Conclusión

El arbol completo representa la expresion:

id + (id * id)  
Esto demuestra que el programa respeta la jerarquia de operadores, dando prioridad a la multiplicacion sobre la suma.
