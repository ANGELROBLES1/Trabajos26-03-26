# Arbol de Sintaxis con Gramatica Libre de Contexto

## Requerimientos

### 1. Archivos necesarios

El programa requiere los siguientes archivos ubicados en la misma carpeta:

punto1.py  
entrada.txt  

El archivo entrada.txt debe contener dos partes:

Primera parte: La gramatica definida mediante reglas de produccion  
Segunda parte: La cadena a evaluar  

Ambas partes deben estar separadas por el simbolo:

%%  

Ejemplo de contenido de entrada.txt:

E -> T Ep  
Ep -> opsuma T Ep | epsilon  
T -> F Tp  
Tp -> opmul F Tp | epsilon  
F -> id | num | pari E pard  

%%  
2+3*(4-5)  

Cada linea antes de %% representa una regla de la gramatica  
La linea despues de %% representa la cadena que sera analizada  


### 2. Abrir la terminal

Abrir una terminal en el sistema operativo Ubuntu  


### 3. Navegar hasta la carpeta del programa

Usar comandos para ubicarse en el directorio donde estan los archivos  

Deben aparecer:

punto1.py  
entrada.txt  


### 4. Ejecutar el programa

Ejecutar el siguiente comando:

python3 punto1.py  


### 5. Funcionamiento del programa

El programa realiza los siguientes pasos:

Lee el archivo entrada.txt  

Separa la gramatica y la cadena usando el simbolo %%  

Construye internamente una estructura de la gramatica donde cada no terminal tiene sus producciones  

Divide la cadena en tokens individuales mediante un proceso de tokenizacion  

Convierte numeros en num, operadores en opsuma u opmul, y parentesis en pari y pard  

Inicia el analisis sintactico desde el simbolo inicial que corresponde a la primera regla de la gramatica  

Aplica un metodo recursivo probando cada produccion posible hasta encontrar una derivacion valida  


## 7. Casos de prueba y analisis

A continuacion se presentan diferentes ejecuciones del programa con sus respectivas capturas y analisis del arbol de sintaxis generado.


### Caso 1 2+3*4

<img width="640" height="400" alt="image" src="https://github.com/user-attachments/assets/1b155e46-04ba-469f-9b0e-d46ba23372f4" />

Analisis:

La expresion es 2+3*4  

El arbol muestra que primero se reconoce el primer numero como un T  

Luego aparece opsuma que representa el operador +  

La segunda parte contiene una multiplicacion dentro de Tp  

Esto indica que la expresion se interpreta como:

num opsuma (num opmul num)  

Es decir:

2 + (3 * 4)  

Se respeta correctamente la precedencia de operadores, donde la multiplicacion tiene mayor prioridad que la suma  


### Caso 2 2+3-4


<img width="642" height="442" alt="image" src="https://github.com/user-attachments/assets/bdb82955-45b9-4f0e-8985-8f091f7d5dfb" />

Analisis:

La expresion es 2+3-4  

El arbol muestra dos operaciones de suma (ya que resta se maneja como opsuma)  

Primero se procesa:

num opsuma num  

Luego se aplica nuevamente opsuma con el tercer numero. Esto genera una estructura encadenada:

(num opsuma num) opsuma num  

Es decir:

(2 + 3) - 4  

El arbol refleja una evaluacion de izquierda a derecha para operadores del mismo nivel  


### Caso 3 2+3*(4-5)

<img width="509" height="558" alt="image" src="https://github.com/user-attachments/assets/6db4e109-b540-4d4e-94b4-7bf67686671e" />

Analisis:

La expresion es 2+3*(4-5)  

El arbol muestra que el parentesis se representa con los simbolos pari y pard  

Dentro del parentesis se genera un nuevo arbol E  

Este subarbol corresponde a la expresion:

num opsuma num  

Es decir:

4 - 5  

Luego esta expresion se multiplica por el valor anterior:

num opmul (expresion)  

Finalmente toda la expresion queda:

num opsuma (num opmul (num opsuma num))  

Es decir:

2 + (3 * (4 - 5))  

El arbol demuestra que los parentesis tienen mayor prioridad y se evaluan primero, seguidos por la multiplicacion y luego la suma  


## Conclusion de los casos de prueba

Los resultados obtenidos demuestran que el analizador sintactico:

- Construye correctamente el arbol de sintaxis  
- Respeta la jerarquia de operadores  
- Maneja correctamente operadores encadenados  
- Soporta expresiones con parentesis  

Esto valida que la implementacion del parser funciona correctamente para la gramatica definida  
