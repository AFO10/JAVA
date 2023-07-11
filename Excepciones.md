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

Si creamos excepciones que heredan desde ```RuntimeException``` es porque "puede" lanzar excepciones, pero si heredamos desde ```Exception``` es porque si o si va a lanzar una excepción en específico. También conocidas como ```checked```, son excepciones comprobadas que de manera obligatoria se deben tomar en cuenta, por el contrario cuando son ```unchecked``` son excepciones que no son obligatorias de tomar en cuenta, es a consideración del programador. 

Las excepciones comprobadas (heredadas de Exception) son utilizadas para indicar situaciones excepcionales que pueden ocurrir y deben ser manejadas de manera explícita en el código, mientras que las excepciones no comprobadas (heredadas de RuntimeException) generalmente indican errores del programador o situaciones inesperadas que no necesitan ser manejadas de forma obligatoria.

Otra manera de lanzar excepciones en el ejemplo a continuación:
* Sin el método try-catch
  En este caso se hace lo siguiente: 
```
public static void metodoPrueba throws MiException () {
	throw new MiException;
}
```
Sin embargo, para que esto funcione, también debe colocarse el ```throws``` en los métodos que implementen  ```metodoPrueba```, y a su vez a los que implementen a este.

## Unchecked y Checked

### Unchecked

Las excepciones que heredan de la clase RuntimeException (y sus subclases) son excepciones no comprobadas. No se requiere que se declaren en la firma del método ni se capturan explícitamente en un bloque try-catch. El manejo de estas excepciones es opcional y el programador puede decidir si quiere o no manejarlas.

### Checked

Las excepciones que heredan de la clase Exception (pero no de RuntimeException) se consideran excepciones comprobadas. Esto significa que el compilador obliga a que se manejen o se declaren en la firma del método donde pueden ocurrir. Esto se logra mediante el uso de la palabra clave throws en la declaración del método o mediante el uso de un bloque try-catch para capturar y manejar la excepción.

## Finally

Cuando trabajamos con conexiones a bases de datos, casi siempre se implementan dos métodos, uno para leer los datos, y otro para cerrar la conexión. Sin embargo, si surge algún problema durante el momento de lectura de datos, es importante cortar la conexión. Pero que sucede cuando ocurre una excepción antes y nos impide el uso del método de cierre? Para este y otros casos más se utiliza la palabra reservada ```finally```.

```finally``` nos permite realizar una acción independientemente de si se ha atrapado o no el error con ```catch```, aquí un ejemplo de su implementación:

```
try {
	con.leerDatos();
} catch(Exception e) {
	e.printStackTrace();
} finally { 
	con.cerrar();	
}
```

Usamos ```finally``` también para evitar la redundancia de código, el código anterior sin la aplicación de ```finally``` es:

```
try {
	con.leerDatos();
	}
catch(IllegalStateException e) {
	con.cerrar();	
}
con.cerrar();
```

Sin embargo, realizar esto puede no ser una buena práctica debido a que puede generar inseguridad y redundancia.

### Uso de ```finally```

Para tener más clara la relación entre ```try```, ```catch``` y ```finally``` es necesario recordar lo siguiente:

* Un ```try``` no puede funcionar solo, necesita de un ```catch``` o de un ```finally```.
* Un ```try``` puede funcionar solo con un ```finally```, ejemplo:
  ```
  try {
  	//staments
  } finally {
	//staments
  }
  ```
  El código anterior compila correctamente.

* No puede haber más de un ```finally```.
* Es obligatorio respetar el orden, ejemplo:
  ```
  try {
  	//staments
  } catch {
	//staments
  } finally {
	//staments
  }
  ```


## Try with resource 

Si necesitas que el objeto haga algo cuando se cierre, como cerrarlo después, usar la interface ```AutoCloseable``` y usar el ```try with resources```.

Ejemplo:

```
try (Conexion con = new Conexion()){
	con.leerDatos();
} catch(IllegalStateException ex) {
	ex.printStackTrace();
}
```

Lo mostrado anteriormente es la aplicación, sin embargo se deben tomar en cuenta lo siguiente:

* Debe colocarse ```throws``` en todos los métodos que implementen.
  ```public static void main(String[] args)throws Exception```
  
* La clase que genera la excepción debe implementar de la interfaz ```AutoCloseable```:
  ```
  public class Conexion implements AutoCloseable{

  	public Conexion() {
  		System.out.println("Abriendo conexion");
   	}

   	public void leerDatos() {
       		System.out.println("Recibiendo datos");
       		throw new IllegalStateException();
   	}

   	public void cerrar() {
       		System.out.println("Cerrando conexion");
   	}

  	@Override
	public void close() throws Exception {
		this.cerrar();	
	}
  }
  ```
  En el método ```close``` usa ```throws``` y ahí se colocan las acciones que se quieren realizar cuando lo que estaba entre paréntesis del ```try```.

* El bloque ```finally``` se crea automáticamente de forma implícita

Un ejemplo de lo mostrado anteriormente sin el uso de ```try with resource``` es:
```
try {
	con = new Conexion();
	con.leerDatos();
} catch(IllegalStateException e) {
	e.printStackTrace();
} finally { 
	System.out.println("Ejecutando finally");
	if (con != null) {
		con.cerrar();	
	}
}
```















