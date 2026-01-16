# Testlib

Testlib es una herramienta hecha y creada por Mike Mirzayanov [testlib](https://github.com/MikeMirzayanov/testlib).

Su objetivo principal es hacer `generator`, `checkers`, `validators`.

Este es una página con fines educativos y hecho para la comunidad en español, principalmente para el 
círculo de estudio ACM Chatper UNSAAC.

## Validator

Es lo principal que se va a abarcar en esta página. Los validators se encargan de revisar si el input de un problema 
están correctos, ya sea si debe ser un número, si el número pertenece a un rango fijo, etc.
La estructura inicial sería lo siguiente

    #include "testlib.h"

    int main(int argc, char * argv[]){
        registerValidation(argc, argv);

        // Contenido del código //

        inf.readEof();
    }


### inf

Como vieron en el código, `inf.readEof();` Es un comando que indica que lea el siguiente elemento y verifica si el elemento es un comando EOF (es decir, si terminó de leer toda la entrada). Ahora el `inf`. es mejor que se vea por el momento como un comando que indica que estamos vamos a hacer una operación de lectura en el input de los tests de un problema.

Aquí vemos las siguientes métodos del `inf`:

Método | Descripción | Ejemplo
:----------- |:-------------:| -----------:
`readInt(a,b, name)`  | Indica que lea un número entero desde a hasta b, donde name indica el nombre de dicha variable, caso verdadero, retorna dicho valor | Right
Left         | Center        | Right