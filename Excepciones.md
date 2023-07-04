Cuando el programa detecta un error, este detiene su ejecución.

Al momento de que se usa "Try", el programa entiende que puede haber un error, y por tanto lo atrapa con "Catch", finalmente el programa continua su ejecución.

Ejemplo:

```
try{

  /* Aquí se colocan los estamentos los cuales se esperan generen un error*/


} catch ( /*se crea un objeto con el tipo de error que se atrapó. Ejemplo: ArithmeticException exception*/  ){

  /* Operaciones a realizar en caso el programa detecte el error.
  * El programa puede lanzar los métodos del objeto "exception"
  * Ejemplo: exception.printStackTrace();
  */

}

/*El programa continúa.*/
```



# Tipos de Excepciones

