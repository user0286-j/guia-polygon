# Validator

Es lo principal que se va a abarcar en esta página. Los validators se encargan de revisar si el input de un problema 
están correctos, ya sea si debe ser un número, si el número pertenece a un rango fijo, etc.
La estructura inicial sería lo siguiente

    #include "testlib.h"

    int main(int argc, char * argv[]){
        registerValidation(argc, argv);

        // Contenido del código //

        inf.readEof();
    }

Como vieron en el código, `inf.readEof();` Es un comando que indica que lea el siguiente elemento y verifica si el elemento es un comando EOF (es decir, si terminó de leer toda la entrada). Ahora el `inf`. es mejor que se vea por el momento como un comando que indica que estamos vamos a hacer una operación de lectura en el input de los tests de un problema.

Aquí vemos las siguientes métodos del `inf`:

## **readInt(a,b,n)/readLong(a,b,n)**

Lee la siguiente entrada de datos, verifica si es un número entero, en caso sea verdadero retorna el valor.

### Parámetros
- `a`: Rango mínimo que puede tomar el valor númerico.
- `b`: Rango máximo que puede tomar el valor númerico.
- `n`: Nombre de la variable. 

### Ejemplo

Dada la siguiente entrada de datos del problema de [codeforces](https://codeforces.com/problemset/problem/4/A).

> En la primera línea y única línea contiene un número entero $w$ ($1 \le w \le 100$). El peso de la sandía comprado por los chicos.

    #include "testlib.h"

    int main(int argc, char * argv[]){
        registerValidation(argc, argv);

        inf.readInt(1, 100, "w");

        inf.readEof();
    }

Para leer números muy grandes, es usar `readLong()`.

## **readLine()**

Lee toda la línea desde la posición actual hasta un `EOLN` que sería un salto de línea. Y posteriormente hace un salto de línea en caso exista. existe un método llamado `readString()` que actua lo mismo.

### Ejemplo

Tomando el ejemplo del problema F del [Cuscontest XXIII](https://codeforces.com/group/gHgjxYvnJD/contest/646498/problem/F).

> Una sola línea, la colección de libros como una secuencia de letras minúsculas del alfabeto inglés, sin espacios, con una longitud máxima de 70 caracteres. Donde cada letra representa un libro.

    #include "testlib.h"

    int main(int argc, char * argv[]){
        registerValidation(argc, argv);

        inf.readLine();

        inf.readEof();
    }

## **readToken()**

Lee un token (cadena de texto), usando como parámetro `regex` (readString() también tiene regex). regex en pocas palabras permite verificar si la cadena de texto es correcto o cumple ciertas condiciones, algunos ejemplos:

- Conjunto de carácteres por ejemplo `[a-z]` indica que pertenece al conjunto del alfabeto inglés en minúscula.
- Conjunto que no pertenezca por ejemplo `[^a-z]` que dice cualquier cosa, menos desde la a hasta la z del alfabeto inglés.
- Puede ser considerado rangos por ejemplo `[a-z]{3,100}` que sería un string de longitud mínima 3 y máximo 100 que consiste solo de carácteres minúscula del alfabeto inglés.
- Puedes utilizar operadores lógicos como `Ismael|Adel`. Indicando que el texto solo es válido si dice `Ismael` o `Adel`.


Tiene otro parámetro que indica el nombre de la entrada que se está leyendo.

### Ejemplo

Tomando el mismo ejemplo del problema F del [Cuscontest XXIII](https://codeforces.com/group/gHgjxYvnJD/contest/646498/problem/F).
Pero esta vez indicando que la máximo son 70 carácteres.

> Una sola línea, la colección de libros como una secuencia de letras minúsculas del alfabeto inglés, sin espacios, con una longitud máxima de 70 caracteres. Donde cada letra representa un libro.

    #include "testlib.h"

    int main(int argc, char * argv[]){
        registerValidation(argc, argv);

        inf.readToken("[a-z]{1,70}", "s");

        inf.readEof();
    }




## **readEoln()**

Verifica si el siguiente elemento del input es un salto de línea.

### Ejemplo

Tomando el ejemplo del problema I del [Cuscontest XXII](https://codeforces.com/group/gHgjxYvnJD/contest/616018/problem/I)

> La primera línea contiene un único número entero t (1≤t≤1000), el número de casos. Cada una de las siguientes t lineas contiene una cadena s (2≤|s|≤200) que representa la contraseña comprimida.

    #include "testlib.h"

    int main(int argc, char * argv[]){
        registerValidation(argc, argv);

        int N = inf.readInt(1, 1000, "N");
        inf.readEoln();

        for (int i = 1; i <= N; ++i){
            inf.readToken("[A-Z1-9]{2,200}");
            inf.readEoln();
        }

        inf.readEof();
    }

## **readSpace()**

Verifica si el siguiente elemento del input es un espacio.

### Ejemplo

Tomando el ejemplo del problema Nohana [Cuscontest XXI-E](https://codeforces.com/group/gHgjxYvnJD/contest/541090/problem/E)

> La primera línea de la entrada contendrá un número entero t (1 ≤ t ≤ 10), que representa el número de casos. A continuación, habrá t líneas, cada una con dos palabras, S1 y S2 (1 ≤ |S1|, |S2| ≤ 200), que representan la ciudad de origen y la ciudad de destino de la escala, respectivamente.

    #include "testlib.h"

    int main(int argc, char * argv[]){
        registerValidation(argc, argv);

        int t = inf.readInt(1,10, "t");
        inf.readEoln();

        for (int i = 1; i <= t; ++i){
            setTestCase(i); // Indica que estamos en un caso de prueba, no es necesario añadir esto
            inf.readToken("[a-z]{1,200}", "a");
            inf.readSpace();
            inf.readToken("[a-z]{1,200}", "b");
            inf.readEoln();
        }

        inf.readEof();
    }

## **readInts(n,a,b)/readLongs(n,a,b)**

Se encarga de leer n enteros separados por un espacio (como por ejemplo `3 2 1`). y verifica si todo está correcto. retorna un `vector<int>`

Para leer números muy grandes es usar `readLongs()`.

### Parámetros

- `n`: Cantidad de números que va a leer. 
- `a`: Rango mínimo que puede tomar el valor númerico.
- `b`: Rango máximo que puede tomar el valor númerico.


### Ejemplo

Tomando como ejemplo el problema Máximo Combo del [Cuscontest XXI-N](https://codeforces.com/group/gHgjxYvnJD/contest/616018/problem/N)

> La primera de la entrada proporciona dos valores, N (1≤N≤40) el número de poderes disponibles para el personaje y D (1≤D≤1012) el máximo daño permitido en el juego. La segunda linea contiene N números enteros separados por espacios, donde cada di (1≤di≤1012) representa el daño individual del i-ésimo poder (1≤i≤n) del personaje.

    #include "testlib.h"

    int main(int argc, char * argv[]){
        registerValidation(argc, argv);

        int N = inf.readInt(1, 40, "N");
        inf.readSpace();
        inf.readLong(1, 10000ll*10000ll*10000ll, "D");
        inf.readEoln();

        inf.readLongs(N, 1, 10000*10000*10000, "a_i");
        inf.readEoln();
        
        inf.readEof();
    }