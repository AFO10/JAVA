
Como se ha visto en capítulos anteriores, Java incluye paquetes de manera implícita. Como es en el caso de ```java.lang``` o ```java.io``` (contiene clases para leer archivos, etc). En esta sección, nos enfocaremos en ```java.util```.

# Conociendo Arrays

Un array en un conjunto de datos, en el que para acceder a un valor de estos datos. Es necesario especificar el índice, que es la posición en que se encuentra ubicado dentro del array.

## Declarando Arrays:

Ejemplo:

```int[] edades = new int[5];```

* Es necesario especificar el tamaño del array, para poder asignarle la memoria.
* Todo array se crea con un tamaño fijo.
* Cuando se crea el array como tipo de datos ```int```, inicializa todos valores del array en ```0```
* Los arrays son objetos, ya que estos se necesitan inicializar.

También es posible declarar un array de forma literal (usando valores directamente). Ejemplo:

```int[] edades = {12, 4, 23, 7, 45};```

## Excepciones Relacionadas con Arrays:

* Cuando queremos acceder a un dato de un array que no existe. Nos dará la excepción ```ArrayIndexOutOfException```.
* No se pueden guardar un tipo de datos distinto a un array. Nos dará la excepción ```ArrayStoreException```.
* Cuando queremos hacer un casteo que no es válido. Nos dará la excepción ```ClassCastException```.
  
## Operaciones
Cuando trabajemos con arrays, nos será posible realizar métodos diversos. A continuación veremos algunos de ellos.

### Tamaño de un array

Se calcula con ```length```. Ejemplo:

```
int[] array = new int[5];
int tamanioArray = array.lenght;
```

### Creación de arrays de diversos tipos

Es posible realizar un arreglo de cualquier tipo de objeto. Ejemplo:
Sin embargo, estos objetos no han sido inicializados. Por lo que se debe tomar precauciones con su uso.

```
CuentaCorriente cc = new CuentaCorriente(23, 44);

CuentaCorriente[] cuentas = new CuentaCorriente[5];
cuentas[0] = cc;
```

Lo que sucede en el código anterior, es que se instancia un objeto de tipo ```CuentaCorriente``` de nombre ```cc```. 
Luego se crea un arreglo que de Cuentas con tamaño 5. Sin embargo las celdas del arreglo no han sido inicializadas. Por lo que tomarían el valor de ```null```, lo que pasa a continuación es que se referencia ```cc``` a ```cuentas[0]```.

# Guardando Referencias

## Cast Objeto 1

Se realiza un casteo cuando queremos hacer una "conversión" de tipo de dato. Esto solo es posible si el casteo es compatible. Ejemplo:

```CuentaCorriente cuenta = (CuentaCorriente) cuentas[1];```

A continuación, algunas cosas a tomar en cuenta antes de realizar un casteo.

* Deben ser entre tipos de datos compatibles entre si. Por ejemplo, en la línea de código anterior, el objeto ```cuentas[1]``` pertenece a un array de tipo ```Cuenta```, sin embargo el valor dentro de ```cuentas[1]``` es de tipo ```CuentaCorriente```, esta declaración fue posible debido a que ```CuentaCorriente``` hereda de ```Cuenta```. Entonces lo que se hizo en la línea de código, fue confirmar que efectivamente ```cuentas[1]``` es de tipo ```CuentaCorriente```, ya que en caso contrario, el programa lo tomaría como un objeto de tipo ```Cuenta```.  

## Cast Objeto 2

Podemos crear un array con valores de diferente tipo, siempre y cuando los valores que esten en el array, extiendan de una clase padre que será el tipo de clase con la que se va a declarar el array. Ejemplo:

```
Object referencias = new Object[5];
referencias[0] = "hola mundo";

Cuenta cuenta = new Cuenta;
referencias[1] = cuenta;

referencias[2] = 2;

...
```

Esto es posible debido a que ```Object``` es la clase padre de todas las clases, entonces es posible crear un array de este tipo y que sus valores sean se diferentes tipos siempre y cuando hereden de la clase padre ```Object```.

## Cast Explícito

```
CuentaCorriente cc1 = new CuentaCorriente(22, 33);
Cuenta Cuenta = (Cuenta) cc1; //cast explícito mas desnecessário
```


## Cast Implícito

```
CuentaCorriente cc1 = new CuentaCorriente(22, 33);
Cuenta cuenta = cc1; //cast implícito
```

## Método main

A continuación veremos para que sirve la línea:

```
public static void main (String[] args)
```

Sirve para poder ingresar comandos via consola. Ejemplo

Si queremos compilar un archivo ```.java``` para bytecode.

```
javac CodigoEjemplo.java
```

Si queremos ejecutar con argumentos

```
java CodigoEjemplo arg1 arg2 arg3 etc
```


