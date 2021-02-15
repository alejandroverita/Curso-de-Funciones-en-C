# CURSO DE FUNCIONES EN C

## FUNCIONES

Una función, es un trozo de código que hace una tarea específica. Esta tarea se puede llamar en varias ocasiones en nuestro código, sin necesidad de repetir código.

Elementos: El retorno, el nombre de la función y argumentos.
El retorno debe corresponder a un tipo concreto. Y es lo que la función debe retornar. Puede darse el caso de que la función no devuelva un valor y entonces se declara de tipo void.
El nombre de la función es la manera de identificar esta función para poderla llamar.

Los argumentos pueden ser void, que no tiene o de un tipo de concreto que será utilizado en la función.

Estructura de una funcion:

    return-type function-name(parameter declartions, if any){
        declarations;
        statemets;
    }
	

## COMO USAR LAS FUNCIONES

Siempre que vayamos a hacer llamados a operaciones es bueno meterlo en funciones. Como en el siguiente caso de la potencia en C. 

Al no haber una expresion matematica que explicitamente llame a una funcion es buena practica crear una funcion que reciba como parametros los datos obligatorios que se necesita en la funcion, en este caso el de la potencia. 


    #include <stdio.h>
    #include <stdlib.h>
    
    //No hay potencia en C por lo que hay que declarar una funcion
    int power(int base, int n);
    
    int main()
    {
        printf("Declarar una potencia en funcion!\n");
    
        int i, n=2;
    
        for(i=0; i<= 10; i++)
        {
            printf("%d ^ %d = %d \n", n, i, power(n, i));
        }
    
        return 0;
    }
    
    int power (int base, int n)
    {
        int i, p;
        p=1;
        for(i=1; i<=n; i++)
        {
            p = p* base;
        }
    
        return p;
    }
    
	
<br>

[========]

## TIPOS DE RETORNO EN FUNCIONES

1. Funciones sin argumentos y sin valor de retorno


    void functionName(); //Declarando la function.
    functionName(); //Invocando o ejecutando a la function
    void functionName()// definicion de la function
    {
      //logica
    }
    
	
2. Funciones con argumentos, pero sin valor de retorno


    void functionName(float); //Declarando la function.
    functionName(float); //Invocando o ejecutando a la function
    void functionName(float) // definicion de la function
    {
      //logica
    }

3. Funciones sin argumentos, pero con valor de retorno


`int functionName();`

4. Funciones que tienen argumentos y valor de retorno


`int functionName(int, float);`


<br>

[========]


## IMPLEMENTACIÓN DE FUNCIONES

Funciones sin argumentos y sin valor de retorno 😄

    void demo();
    
    int main()
    {
      demo();
    
      return 0;
    }
    
    void demo()
    {
     int a, b, suma;
     a = 100;
     b = 100;
     printf("El resultado es %i", suma);
    }


Funciones con argumentos, pero sin valor de retorno


    int a, b;
    
    void sum(int a, int b);
    
    int main()
    {
      sum(100, 100);
    
      return 0;
    }
    
    void sum(int a, int b)
    {
     int sum;
     sum = a + b;
     printf("El resultado es %i", sum);
    }


Funciones que tienen argumentos y valor de retorno

    int a, b;
    
    int sum(int a, int b);
    
    int main()
    {
      sum(100, 100);
      printf("El resultado es %i", sum(100, 100));
      return 0;
    }
    
    int sum(int a, int b)
    {
     int sum;
     sum = a + b;
     return sum;
    }
<br>

[========]
## PARÁMETROS POR VALOR

- pasar un argumento por referencia, se modifica porque recibe la posición de memoria donde está el valor.

- pasar un argumento por valor, no se modifica porque es una copia, es decir es una posición de memoria diferente.
Un **Puntero **es un argumento por referencia.


    # include <stdio.h>
    int power(int base, int n);
    
    int main()
    {
        int n;
        n = 12;
    
        printf("n = %d resultado de la potencia = %d \n", n, power(2,n));
        
        printf("El valor del exponiente n original siguie siendo: %d \n", n);
    
        return 0;
    }
    
    int power(int base, int n)
    {
        int p;
    
        for (p = 1; n > 0; n--)
        {
            p = p*base;
            printf("El valor temporal de n es: %d \n", n);
        }
    
        return p;
    }

<br>

[========]

## PRINCIPALES BIBLIOTECAS DE C


`#include <stdio.h> //input y output teclado, para imprimir pantalla printf`

`#include <conio.h> //entradas y salidas comunicarnos en la consola`

`#include <string.h> // cuando se trabaja con cadenas de caracteres`

    #include <stdlib.h> system comunicarnos afuera de c con sistema attoy convertir string a entero  adol convierte a long ran genera numeros enteros aleatorios delay para pausa
    
`#include <math.h> // sin cosh floor ceil sqrt`

`#include <time.h>  // para fechas o tiempos del sistema `

`#include <ctype.h> //  tipo manejo de caracteres individuales`

    #include <signal.h> //señales en programa por ejemplo enventos en el teclado , detectar un 	espacio en blanco en cadena de caracteres, detectar caracter en minuscúla lower y upper.


    #include <locale.h> // cuestinones locales al software cuando se neccesita que se adapte al lugar que se use


`#include <errno.h>// para debug errores.`


     #include <assert.h> //macro para verificar asumsiones y imprimir que esta pasando.
    


[Librerias](https://devdocs.io/c/ "Librerias")



<br>

[========]

## MATH.H

Libro “C Programming Language” escrito por Brian W. Kernighan y Dennis M. Ritchie (Creador del lenguaje C)
C Programming Language, 2nd Edition

[C library Math.h](https://www.tutorialspoint.com/c_standard_library/math_h.htm "C library Math.h")
<br>

[========]

## STRING.H

- strlen: devuelve la longitud del string.

- strcpy: recibe dos parámetros, el segundo se copia y se guarda dentro del primero.

Cuando no se quiere realizar la operación con el _string _entero se utilizan las funciones con una n en medio del nombre: strncat, strncpy, strncmp,… Éstas funciones reciben un parámetro más que es la longitud del string con la que se va a operar.

Un ejemplo de esto:

    #include <stdio.h>
    #include <string.h>
    
    char string1[60];
    char string2[60];
    
    int main()
    {
    
        printf("Type a sentence: \n");
        gets(string1);
        printf("Type another sentence: \n");
        gets(string2);
    
        strrev(string1);
        printf("Reversed string: %s \n", string1);
    
        if ( strcmp(string1, string2) == 0)
            printf("The strings are equal \n");
        else
        {
            strcat(string1, string2);
            printf("The strings are different \n");
            printf("The strings joined: %s \n", string1);
            
        }
    
        printf("%d \n", strlen(string1));
    
        strcpy(string1, "New string1");
        printf("%s \n", string1);
    
        strncpy(string1, "New string 1", 4);
        string1[4] = '\0';
        printf("%s \n", string1);
        
        return 0;
    }

[string.h](https://www.tutorialspoint.com/c_standard_library/string_h.htm "string.h")
<br>

[========]

