Memoria HEAP:  Es la memoria en la cual se guardan todos los objetos que creamos en nuestro programa.

Errores que se lanzan sobre la JVM (Java Virtual Machine).

La interface Throwable implementa a Exception y Error:
Por lo que no se puede crear una excepción que herede directamente de Throwable.


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

### Métodos que pueden usar las excepciones:

* **printStackTrace()**: este método nos indica la pila de ejecución, ejemplo:
  ```
  MiException: Mi excepción fue lanzada.
	at Flujo.metodo2(Flujo.java:32)
	at Flujo.metodo1(Flujo.java:19)
	at Flujo.main(Flujo.java:10)
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

```
public static void metodo2() {
	System.out.println("Inicio de metodo2");
	throw new ArithmeticException();                                           
}

```

Throw solo permite "lanzar" objetos que son excepciones, no admite otro tipo de objeto.

## Creando Excepciones

Para esto es necesario crear una clase que extienda de "RuntimeException".
Es necesario definir los constructores con ```super()```

Ejemplo:

```
public class MiException extends RuntimeException{
	
	public MiException() {
		super();
	}

	public MiException(String message) {
		super(message);
	}
}
```

Aplicando lo anterior, entonces la siguiente línea es correcta:

```
	throw new MiException("Mi excepción fue lanzada.");
```

Aplicando lo explicado anteriormente:
```
public class Main {

	public static void metodoPrueba () {
		throw new MiException;
	}

	public static void main (String[] args) {

		try {
			metodoPrueba();
		} catch( MiException exception){
			System.out.println("Excepcion atrapada");
		}	
	}

}

```

La salida que nos da:

```
Excepcion atrapada
```

## Lanzando Excepciones desde Exception

Otra manera de lanzar excepciones:
* Sin el método try-catch
  En este caso se hace lo siguiente: 
```
public static void metodoPrueba throws MiException () {
	throw new MiException;
}
```
Sin embargo, para que esto funcione, también debe colocarse el ```throws``` en los métodos que implementen  ```metodoPrueba```, y a su vez a los que implementen a este.

