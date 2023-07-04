Memoria HEAP:  Es la memoria en la cual se guardan todos los objetos que creamos en nuestro programa.


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

  exception.printStackTrace();  // Indica el estado de la pila de ejecución en que fue encontrado el error


  /* Si el catch anterior no captura el error. Es posible agregar otro catch.
  * Siempre y cuando sea un tipo diferente de excepción
  */
} catch (NullPointerException exception) {

  /* Estamentos*/
}

/*El programa continúa.*/
```

Otro caso:

```
try{

  /* Estamentos */


/* Es posible colocar 2 tipos de excepciones en un mismo catch*/
} catch (ArithmeticException | NullPointerException exception){


} 

/*El programa continúa.*/
```

## Lanzando Excepciones

Si queremos lanzar errores. Es necesario lo siguiente:

```

	public static void metodo2() {
		System.out.println("Inicio de metodo2");

/* No será suficiente con crear el objeto ae.
* Sino, es necesario usar la palabra reservada "throw" para lanzar este error.
*/
		ArithmeticException ae = new ArithmeticException(); // Se crea el objeto Excepción
    throw ae;                                           // Se lanza la excepción
/* throw no permite que haya más código debajo de la línea en que se encuentra, en el método que se está llamando.
Pues al lanzar el error, todo lo que venga después no será realizado. Esto se limita al método en que se encuentre.
*/
	
	}

```


Otra manera de hacerlo:

	public static void metodo2() {
		System.out.println("Inicio de metodo2");
```
    throw new ArithmeticException();                                           

	}

```

Throw solo permite "lanzar" objetos que son excepciones, no admite otro tipo de objeto.
