Recapitular y explicar de manera resumida como funciona las clases y objetos.

Explicar sobre el objeto **String**:

 1. **Objetos `String` y referencias:** En Java, los objetos `String` se almacenan en el heap, y las variables que hacen referencia a esos objetos contienen la dirección de memoria donde se almacena el objeto `String`. La capacidad de hacer referencia a objetos `String` permite el uso de funciones sofisticadas y operaciones complejas en cadenas de texto.
    
2. **Tipos primitivos numéricos y lógicos:** Estos tipos, como `int`, `byte`, `double` y `boolean`, se utilizan para almacenar valores simples y fijos en la memoria. No se almacenan en el heap, sino en la pila (stack) de memoria, lo que los hace más eficientes en términos de velocidad y rendimiento. Estos tipos primitivos *son intrínsecos al lenguaje* y no se comportan como objetos. Esto significa que no pueden llamar métodos ni tienen las características de los objetos, como la capacidad de heredar o implementar interfaces.

#### Ejemplos a presentar:

```
int n1 = 7;
int n2 = 7;

System.out.println(n1 == n2); // true
```

En cambio:
```
String text1 = new String("hola");
String text2 = "hola";

System.out.println(text1 == text2); // false
```

#### Por que pasa esto?
Esto pasa por el String Pool una característica de optimización implementada por la JVM (Máquina Virtual de Java) para reducir la duplicación de cadenas y ahorrar memoria.

Si la *cadena ya existe*, la referencia apuntará a la misma ubicación de memoria, lo que hace que las referencias de ambas variables sean iguales.

**Referencias** = String y tipos 
**Numericos**  = int, double, byte, char, etc...
**Logicos**  = boolean

```
int num1 = 5; // Variable local num1 se almacena en la pila 
int num2 = 10; // Variable local num2 se almacena en la pila 
int sum = num1 + num2; // El resultado se almacena en la pila System.out.println("La suma es: " + sum);
```


### CREANDO UNA CLASE
```
public class Persona {
	int dni;
	String nombre;
	String apellido;
	
	public void mostrarDatos() {
		System.out.println(dni);
		System.out.println(nombre);
		System.out.println(apellido);
	}
}
```

### IDENTIDAD

El hecho de tener dos variables de tipo clase no significa tener dos objetos.
```
Persona p1 = new Persona();

p1.dni = 71252632;
p1.nombre = "Dante";
p1.apellido = "Vilchez";

System.out.println(p1);

Persona p2; // no es objeto, es una varianle

p2 = p1;
p2.nombre = "Juan";

System.out.println(p1);
```

Seguidamente vemos que estamos *accediendo directamente* a los atributos del objeto.
y **eso está mal**, por el hecho de que no existe un control en la forma en la que modifcamos los datos de la clase, y esto trae un poblema de integridad al no haber una validacion de la informacion ingresada. Y es aquí donde entra en juego un concepto llamado encapsulamiento.

### ¿Qué es el encapsulamiento?
Es un uno de los 4 pilares de la POO, que implica ocultar los detalles internos de una clase y proporcionar solo métodos específicos para acceder y modificar los datos dentro de esa clase.


### Ventajas del encapsulamiento:
1. **Control de acceso:** Prevenir modificaciones no deseadas y a garantizar que los datos de la clase solo se modifiquen de maneras controladas.
    
2. **Integridad:**  Cualquier modificación a los atributos debe realizarse a través de métodos de acceso, lo que permite la validación y aplicación de reglas específicas antes de realizar cambios en los datos.
    
3. **Flexibilidad y mantenibilidad:** Al *ocultar los detalles de implementación* de la clase, permite la posibilidad de realizar cambios internos sin afectar el código que utiliza la clase.
    
4. **Modularidad y reutilización:** Las clases que utilizan la clase encapsulada solo necesitan conocer la interfaz proporcionada por la clase, lo que facilita la reutilización de la clase en diferentes contextos y aplicaciones.

***El tipo ejemplo del coche.***

Veamos esto, para lograr encapsular una clase es necesario conocer los modificadores de acceso:
### Modificadores de acceso

Tenemos:
**public:** por defecto ya está en public y permite acceso publico
**private:** solo puede acceder la misma clase
**protected:** permite acceso a la misma clase y a sus hijas

De momento solo usaremos private y public.
Los atributos de una clase deben se private, por lo que el acceso a ellas y su modificacion se da por de metodos.
### Metodos getters y setters
- Hacerlo manualmente
- Autocompletado de eclipse


``` getter y setter

public int getDni() {
	return dni;
}

public void setDni(int dni) {
	this.dni = dni;
}

public String getNombre() {
	return nombre;
}

public void setNombre(String nombre) {
	this.nombre = nombre;
}

public String getApellido() {
	return apellido;
}

public void setApellido(String apellido) {
	this.apellido = apellido;
}
```
- Explicar el "*this*" en los setters.
	Agregamos un **sysout** más al metodo mostrarDatos():
	```
	System.out.println(this); // nos arroja el identificador
	```

	Sin el *this* no se puede modificar a los atributos solo se estaria agregando el el parametro a si mismo.
	- El *this* apunta a las instancia de la clase, ya que si usamos en su lugar el nombre de la clase, este solo puede usar su metodos y atributos staticos, por lo que en metodos estaticos no podemos acceder a *this*.

### Constructores
tenemos este problema:
```
Persona p1 = new Persona();
p1.setDni(72152761);
p1.setNombre("dante");
p1.setApellido("Vilchez");

Persona p2 = new Persona();
p2.setDni(76152162);
p2.setNombre("Javier");
p2.setApellido("Rodriguez");
```
Es aquí donde entran los constructores.
- Cada que hacemos un new Persona(), java, implicitamente, está que llama al contructor.
- Solo es posible invocar aal constructor una sola vez que es cuando se crea el objeto.

### Sobrecarga de contrutores
- No podemos estables dos contrcutores que reciban la misma cantidad de parametros y a su vez del mismo tipo en orden.

```
public Persona(int dni, String nombre, String apellido) {
	this.dni = dni;
	this.nombre = nombre;
	this.apellido = apellido;
}

public Persona(int dni, String nombre) {
	setDni(dni);
	setNombre(nombre);
}
```
**Usos del this en contructores**.
```
public Persona (String nombre) {
	this(8962267, nombre); // uso del constr. que recibe dos parametros
}
```

### Sobrecarga de metodos.
Tal vez no dé tiempo....
Explicar la importancia de la sobrecarga de metodos.

### Constantes
**Static** 