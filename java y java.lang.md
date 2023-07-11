
# Modificadores de Acceso

Los modificadores de acceso modifican el alcance de las variables en un proyecto.
Son los siguiente:

* public: no importa donde esté, es accesible.
* default: solo visible a nivel de paquete.
* protected: solo visible a nivel de paquete y que sean hijas de la clase.
* private: solo es posible tener acceso dentro de la clase.

Cuando una clase no tiene o no específica un modificador de acceso, tendrá a ```default``` lo que indica que será vista únicamente en el paquete donde esté.

# Distribución de Código

## Documentación javadoc

La documentación de un código permite a un usuario externo poder apreciar una descripción de la clase.

Se puede tanto documentar a nivel de clase, como a nivel de los métodos.

Es una documentación técnica.

## Generando javadoc

Cuando se quiere documentar, se realizar de la siguiente manera:

* Documentación a nivel de clase:
  ```
  /**
   * Cuenta va a crear instancias de CuentaCorriente
   *
   * @version 1.0
   * @author Marakim
   *
   */

   public abstract class Cuenta {
   //
   }
  ```

* Documentación a nivel de métodos:
  ```
  /**
   * Este método retira dinero de la cuenta y si ocurre un error devuelve una excepción
   * @param agencia
   * @parem numero
   * @throws MiException
   */
  public void cuenta (int agencia, int numero) throws MiException {

  ```

Para poder apreciar la documentación, que está como javadoc. Se realiza lo siguiente:
```Window``` -> ```Show view``` -> ```Others``` -> ```Javadoc```

![image](https://github.com/AFO10/JAVA/assets/89848233/c8a62fe7-e643-4d12-bae1-8aa713ea0150)


Para poder generar el javadoc, es necesario tener el JDK (Java development kit).
```Project``` -> ```Generate Javadoc```

![image](https://github.com/AFO10/JAVA/assets/89848233/9f41cac9-8454-47df-be2d-9ae175767fd9)

Nos proporcionará una carpeta ```doc``` en la cual habrán varios archivos ```html``` donde podremos apreciar la documentación.

![image](https://github.com/AFO10/JAVA/assets/89848233/de5f7eb1-9895-4b87-8b2c-1747f748aed0)

### Etiquetas en javadoc

Lista completa de los tags en javadoc:

* @author (usado en la clase o interfaz)
* @version (usado en la clase o interfaz)
* @param (usado en el método y constructor)
* @return (usado solo en el método)
* @exception o @throws (en el método o constructor)
* @see
* @since
* @serial
* @deprecated

## Archivos JAR


