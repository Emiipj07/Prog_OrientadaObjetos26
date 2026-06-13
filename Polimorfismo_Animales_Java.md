# Polimorfismo en Java - Ejemplo de Animales

## Problema que resuelve

El polimorfismo permite que diferentes objetos respondan al mismo método de formas distintas.

En este ejemplo todos los animales tienen el método `hacerSonido()`, pero cada uno produce un sonido diferente.

Además, se muestra:

- Polimorfismo en tiempo de ejecución (sobreescritura).
- Polimorfismo en tiempo de compilación (sobrecarga).

---

# Clase Animal

```java
abstract class Animal {

    public abstract void hacerSonido();

    // Sobrecarga de métodos (polimorfismo en compilación)
    public void mostrarInfo() {
        System.out.println("Animal registrado");
    }

    public void mostrarInfo(String nombre) {
        System.out.println("Animal: " + nombre);
    }
}
```

---

# Clase Perro

```java
class Perro extends Animal {

    @Override
    public void hacerSonido() {
        System.out.println("Guau");
    }
}
```

---

# Clase Gato

```java
class Gato extends Animal {

    @Override
    public void hacerSonido() {
        System.out.println("Miau");
    }
}
```

---

# Clase Pajaro

```java
class Pajaro extends Animal {

    @Override
    public void hacerSonido() {
        System.out.println("Pio");
    }
}
```

---

# Clase Vaca

```java
class Vaca extends Animal {

    @Override
    public void hacerSonido() {
        System.out.println("Muu");
    }
}
```

---

# Clase Caballo

```java
class Caballo extends Animal {

    @Override
    public void hacerSonido() {
        System.out.println("Hiii");
    }
}
```

---

# Clase Main

```java
public class Main {

    public static void main(String[] args) {

        Animal a1 = new Perro();
        Animal a2 = new Gato();
        Animal a3 = new Pajaro();
        Animal a4 = new Vaca();
        Animal a5 = new Caballo();

        System.out.println("=== Polimorfismo en tiempo de ejecucion ===");

        a1.hacerSonido();
        a2.hacerSonido();
        a3.hacerSonido();
        a4.hacerSonido();
        a5.hacerSonido();

        System.out.println("\n=== Polimorfismo en tiempo de compilacion ===");

        a1.mostrarInfo();
        a1.mostrarInfo("Perro");
    }
}
```

---

# ¿Dónde está el polimorfismo?

## 1. Polimorfismo en tiempo de compilación

Se produce mediante la sobrecarga de métodos.

```java
mostrarInfo()
mostrarInfo(String nombre)
```

Los métodos tienen el mismo nombre pero diferentes parámetros.

El compilador decide cuál ejecutar.

---

## 2. Polimorfismo en tiempo de ejecución

Se produce mediante la sobreescritura.

```java
Animal a1 = new Perro();
a1.hacerSonido();
```

Aunque la referencia es de tipo `Animal`, Java ejecuta el método de la clase real (`Perro`).

Lo mismo ocurre con Gato, Pajaro, Vaca y Caballo.
