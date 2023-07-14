
Como se ha visto en capítulos anteriores, Java incluye paquetes de manera implícita. Como es en el caso de ```java.lang``` o ```java.io``` (contiene clases para leer archivos, etc). En esta sección, nos enfocaremos en ```java.util```.

# Conociendo Arrays

Un array en un conjunto de datos, en el que para acceder a un valor de estos datos. Es necesario especificar el índice, que es la posición en que se encuentra ubicado dentro del array.

## Declarando Arrays:

Ejemplo:

```int[] edades = new int[5]```

* Es necesario especificar el tamaño del array, para poder asignarle la memoria.
* Todo array se crea con un tamaño fijo.
* Cuando se crea el array como tipo de datos ```int```, inicializa todos valores del array en ```0```
* Los arrays son objetos, ya que estos se necesitan inicializar.

## Excepciones Relacionadas con Arrays:

* Cuando queremos acceder a un dato de un array que no existe. Nos dará la excepción ```ArrayIndexOutOfException```.
  
## Operaciones
Cuando trabajemos con arrays, nos será posible realizar métodos diversos. A continuación veremos algunos de ellos.

### Tamaño de un array

Se calcula con ```length```. Ejemplo:

```
int[] array = new int[5];
int tamanioArray = array.lenght;
```
