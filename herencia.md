# Herencia

## Ejemplo: Estudiante y Becario

En este ejemplo, la clase `Becario` hereda los atributos y métodos de la clase `Estudiante`.

### Clase Padre: Estudiante

```java
public class Estudiante {
    protected String nombre;

    public Estudiante(String nombre) {
        this.nombre = nombre;
    }

    public void estudiar() {
        System.out.println(nombre + " está estudiando");
    }
}
```

### Clase Hija: Becario

```java
public class Becario extends Estudiante {

    public Becario(String nombre) {
        super(nombre);
    }

    public void recibirBeca() {
        System.out.println(nombre + " recibe una beca");
    }
}
```

### Clase Principal

```java
public class Main {
    public static void main(String[] args) {

        Becario alumno = new Becario("Ana");

        alumno.estudiar();      // Método heredado
        alumno.recibirBeca();   // Método propio
    }
}
```

### Salida

```text
Ana está estudiando
Ana recibe una beca
```

## Explicación

- `Estudiante` es la **clase padre**.
- `Becario` es la **clase hija**.
- La palabra clave `extends` permite la herencia.
- `Becario` hereda el atributo `nombre`.
- `Becario` hereda el método `estudiar()`.
- `Becario` agrega su propio método `recibirBeca()`.

### Relación "es un"

Un **Becario es un Estudiante**, por lo que puede heredar sus características y comportamientos.
