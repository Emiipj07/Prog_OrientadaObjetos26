# Polimorfismo 

![Polimorfismo](Polimorfismo_info.png)

**Recuerda:** El polimorfismo permite que diferentes objetos respondan al mismo método de formas distintas.

## Ejemplo: 
Todos los pokemones tienen el método `atacar()`, pero cada uno produce un ataque diferente.

![Pokemon](ejemploPokemon.png)

---

# Clase Pokemon

```java
abstract class Pokemon {

    public abstract void atacar();

    // Polimorfismo en tiempo de compilación (sobrecarga)
    public void mostrarInfo() {
        System.out.println("Pokemon registrado");
    }

    public void mostrarInfo(String nombre) {
        System.out.println("Pokemon: " + nombre);
    }
}
```

---

# Clase Charizard

```java
class Charizard extends Pokemon {

    @Override
    public void atacar() {
        System.out.println("Lanzallamas");
    }
}
```

---

# Clase Blastoise

```java
class Blastoise extends Pokemon {

    @Override
    public void atacar() {
        System.out.println("Hidrobomba");
    }
}
```

---

# Clase Venosaur

```java
class Venusaur extends Pokemon {

    @Override
    public void atacar() {
        System.out.println("Rayo Solar");
    }
}
```

---

# Clase Gengar

```java
class Gengar extends Pokemon {

    @Override
    public void atacar() {
        System.out.println("Bola Sombra");
    }
}
```

---

# Clase Main

```java
public class Main {

    public static void main(String[] args) {

        Pokemon p1 = new Pikachu();
        Pokemon p2 = new Charizard();
        Pokemon p3 = new Blastoise();
        Pokemon p4 = new Venusaur();
        Pokemon p5 = new Gengar();

        System.out.println("=== POLIMORFISMO EN TIEMPO DE EJECUCION ===");

        p1.atacar();
        p2.atacar();
        p3.atacar();
        p4.atacar();
        p5.atacar();

        System.out.println("\n=== POLIMORFISMO EN TIEMPO DE COMPILACION ===");

        p1.mostrarInfo();
        p1.mostrarInfo("Pikachu");
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
