# Tipos de Excepciones

Cuando el programa detecta un error, este detiene su ejecución.

Al momento de que se usa "Try", el programa entiende que puede haber un error, y por tanto lo atrapa con "Catch", finalmente el programa continua su ejecución.

Ejemplo:

```
try{

  /* Aquí se colocan los estamentos los cuales se esperan generen un error*/


} catch ( /*se crea un objeto con el tipo de error que se atrapó. Ejemplo: ArithmeticException "exception" */  ){

  /* Operaciones a realizar en caso el programa detecte el error.
  * El programa puede lanzar los métodos del objeto "exception"
  * Ejemplo: exception.printStackTrace();
  */

}

/*El programa continúa.*/
```
Otro caso:

```
try{

  /* Estamentos*/


} catch (ArithmeticException exception){

  exception.printStackTrace();  // Indica el estado de la pila de flujo en que fue encontrado el error


  /* Si el catch anterior no captura el error. Es posible agregar otro catch.
  * Siempre y cuando sea un tipo diferente de excepción
  */
} catch (NullPointerException exception) {

  /* Estamentos*/
}

/*El programa continúa.*/
```

Otro caso;

```
try{

  /* Estamentos */


/* Es posible colocar 2 tipos de excepciones en un mismo catch*/
} catch (ArithmeticException | NullPointerException exception){


} 

/*El programa continúa.*/
```


