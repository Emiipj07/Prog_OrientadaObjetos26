# Taller Grupal - Principios SOLID
- **Integrantes:** Fabio Tapia, Jhostin Molina y Emilia Peña. 

### **Objetivo:** Diseñar e implementar un sistema orientado a objetos aplicando los principios SOLID para mejorar la mantenibilidad, reutilización y escalabilidad del software.
### **Contexto del Problema:** La organización del Mundial de Fútbol necesita desarrollar un sistema para gestionar los procesos del torneo. El sistema debe administrar:
- Participantes
- Registro de actividades
- Reportes
- Notificaciones
- Almacenamiento de información
## Diagrama UML
![DiagramaUML](.png)

## Código 
```java
package mundialsolid;

public class Participante {
    private int id;
    private String nombre;
    private String nacionalidad;

    public Participante(int id, String nombre, String nacionalidad) {
        this.id = id;
        this.nombre = nombre;
        this.nacionalidad = nacionalidad;
    }

    public int getId() {
        return id;
    }

    public String getNombre() {
        return nombre;
    }

    public String getNacionalidad() {
        return nacionalidad;
    }

    public void mostrarInfo() {
        System.out.println("ID: " + id);
        System.out.println("Nombre: " + nombre);
        System.out.println("Nacionalidad: " + nacionalidad);
    }
}
```
### Clase participante 
La clase Participante funciona como una plantilla estructurada para modelar de forma segura a cualquier integrante del mundial mediante el uso de encapsulamiento, protegiendo sus datos (id, nombre y nacionalidad) bajo atributos privados que solo se pueden asignar al crear el objeto mediante su constructor y leerse de forma externa a través de métodos getters de solo lectura; además, cumple con el Principio de Responsabilidad Única (SRP) al encargarse exclusivamente de almacenar esta información y ofrecer el método mostrarInfo para imprimir su propio estado en consola, delegando cualquier otra lógica del 
torneo a clases externas.

### La clase participante hereda 
## Jugador
## Codigo
```java
package mundialsolid;

public class Jugador extends Participante {
    private String posicion;

    public Jugador(int id, String nombre, String nacionalidad, String posicion) {
        super(id, nombre, nacionalidad);
        this.posicion = posicion;
    }

    @Override
    public void mostrarInfo() {
        super.mostrarInfo();
        System.out.println("Posición: " + posicion);
    }
}
```
La clase Jugador hereda todos los atributos y métodos de la clase Participante aplicando el concepto de herencia en programación orientada a objetos, lo que le permite reutilizar la lógica de id, nombre y nacionalidad sin tener que duplicar código. Esta subclase añade un atributo privado propio llamado posicion para guardar el rol específico del futbolista en la cancha, el cual se inicializa en su constructor llamando primero al constructor de la clase padre mediante la instrucción super. Además, implementa el polimorfismo al sobrescribir el método mostrarInfo con la anotación Override, logrando que primero se ejecute la impresión de los datos generales del participante y luego se complemente de forma automática imprimiendo la posición en la consola.

### La clase participante hereda 
## Entrenador
## Codigo
```java
package mundialsolid;

public class Entrenador extends Participante {

    private String especialidad;

    public Entrenador(int id, String nombre, String nacionalidad, String especialidad) {
        super(id, nombre, nacionalidad);
        this.especialidad = especialidad;
    }

    @Override
    public void mostrarInfo() {
        super.mostrarInfo();
        System.out.println("Especialidad: " + especialidad);
    }
}
```
La clase Entrenador hereda todos los atributos y comportamientos de la clase Participante mediante el concepto de herencia, lo que permite reutilizar limpiamente la lógica de id, nombre y nacionalidad sin repetir código. Esta subclase extiende la funcionalidad original al añadir un atributo privado específico llamado especialidad para almacenar el enfoque táctico o técnico del director técnico, el cual se inicializa en el constructor invocando primero al constructor de la clase base con la instrucción super. Asimismo, aplica el polimorfismo al sobrescribir el método mostrarInfo utilizando la anotación Override, lo que permite que al llamarse este método primero se imprima la información general del participante y de inmediato se complemente mostrando la especialidad en la consola.

### La clase participante hereda 
## Arbitro
## Codigo
```java
package mundialsolid;

public class Arbitro extends Participante {

    private String categoria;

    public Arbitro(int id, String nombre, String nacionalidad, String categoria) {
        super(id, nombre, nacionalidad);
        this.categoria = categoria;
    }

    @Override
    public void mostrarInfo() {
        super.mostrarInfo();
        System.out.println("Categoría: " + categoria);
    }
}
```
La clase Arbitro extiende a la clase Participante a través del mecanismo de herencia, lo que le permite adoptar y reutilizar de manera automática los campos de id, nombre y nacionalidad sin necesidad de volver a escribirlos. Esta subclase introduce un campo privado propio denominado categoria para registrar el nivel o rango del colegiado en el torneo, asignando su valor en el constructor tras delegar la inicialización de los datos básicos al constructor padre mediante la palabra clave super. Finalmente, implementa el polimorfismo al rediseñar el comportamiento del método mostrarInfo con la anotación Override, logrando que el sistema imprima primero los datos generales heredados y añada al final la línea específica con la categoría del árbitro en la consola.
