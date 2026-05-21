# Reporte del Sistema de Inventario RetroGaming

**Emilia E. Peña**

**Fecha: 21-05-2026**

---

# Desarrollo del Taller: Serialización de Objetos en Java

## 1. Objetivo

Desarrollar una aplicación de consola en Java para gestionar el inventario de una tienda de videojuegos clásicos llamada **RetroGaming**, aplicando conceptos de programación orientada a objetos como encapsulamiento, clases, objetos, colecciones y persistencia de datos mediante **serialización**.

---

# 2. Descripción del problema

La tienda RetroGaming necesita almacenar su catálogo de videojuegos de forma permanente para evitar que la información se pierda cuando el programa se cierre.

Para solucionar este problema se implementó un sistema que permite:

* Registrar videojuegos.
* Guardar videojuegos en memoria temporal usando una lista (`ArrayList`).
* Serializar los datos en un archivo binario (`inventario.dat`).
* Recuperar los datos almacenados mediante deserialización.

---

# 3. Diseño de Clases

## Clase `Main`

Permite ingresar los videojuegos con su respectiva información y ejecuta el resto de funciones.

```java
package retrogaming;

import java.util.Scanner; 

public class RetroGaming {

    public static void main(String[] args) {
        Scanner entrada = new Scanner(System.in);
        Inventario inventario = new Inventario();
        
        System.out.println("         RETROGAMING         ");
        System.out.println("==============================");
        System.out.println("--- SISTEMA DE INVENTARIO ---");
        System.out.println();
        int n; 
        System.out.print("Cantidad de videojuegos a registrar: ");
        n = entrada.nextInt();
        entrada.nextLine(); 
        
        for (int i = 1; i <= n; i++) {
            System.out.println("\nIngrese los datos del videojuego " + i);
            System.out.print("Título: ");
            String titulo = entrada.nextLine();
            System.out.print("Plataforma: ");
            String plataforma = entrada.nextLine();
            System.out.print("Año de lanzamiento: ");
            int anio = entrada.nextInt();
            System.out.print("Precio: ");
            double precio = entrada.nextDouble();
            entrada.nextLine(); 
            Videojuego juego = new Videojuego(titulo, plataforma, anio, precio);
            inventario.agregarVideojuego(juego);
        }
        System.out.println("Inventario actualizado correctamente!");

        System.out.println("\n=== INVENTARIO ORIGINAL ===");
        inventario.listarInventario();

        inventario.guardarDatos("inventario.dat");

        System.out.println("\n--- Reiniciando sistema ---");
        Inventario nuevoInventario = new Inventario();

        nuevoInventario.cargarDatos("inventario.dat");

        System.out.println("\n=== INVENTARIO RECUPERADO ===");
        nuevoInventario.listarInventario();

        entrada.close();
    }
}
```
---

## Clase `Videojuego`

Representa cada videojuego dentro del inventario.

### Atributos

* `titulo` → nombre del videojuego.
* `plataforma` → consola o plataforma del juego.
* `anioLanzamiento` → año de lanzamiento.
* `precio` → costo del videojuego.

### Métodos implementados

* Constructor para inicializar atributos.
* Métodos Getters y Setters para encapsulamiento.
* `mostrarInformacion()` para imprimir los datos del videojuego.

```java
package retrogaming;

import java.io.Serializable;

public class Videojuego implements Serializable {

    private String titulo;
    private String plataforma;
    private int anioLanzamiento;
    private double precio;

    public Videojuego(String titulo, String plataforma, int anioLanzamiento, double precio) {
        this.titulo = titulo;
        this.plataforma = plataforma;
        this.anioLanzamiento = anioLanzamiento;
        this.precio = precio;
    }

    public String getTitulo() {
        return titulo;
    }

    public String getPlataforma() {
        return plataforma;
    }

    public int getAnioLanzamiento() {
        return anioLanzamiento;
    }

    public double getPrecio() {
        return precio;
    }

    public void setTitulo(String titulo) {
        this.titulo = titulo;
    }

    public void setPlataforma(String plataforma) {
        this.plataforma = plataforma;
    }

    public void setAnioLanzamiento(int anioLanzamiento) {
        this.anioLanzamiento = anioLanzamiento;
    }

    public void setPrecio(double precio) {
        this.precio = precio;
    }

    public void mostrarInformacion() {
        System.out.println("Título: " + titulo);
        System.out.println("Plataforma: " + plataforma);
        System.out.println("Año: " + anioLanzamiento);
        System.out.println("Precio: $" + precio);
        System.out.println("---------------------------");
    }
}
```

---

## Clase `Inventario`

Administra la colección de videojuegos.

### Atributo principal

* `ArrayList<Videojuego> videojuegos`

### Métodos implementados

* `agregarVideojuego()` → agrega un videojuego al inventario.
* `listarInventario()` → muestra todos los videojuegos registrados.
* `guardarDatos()` → serializa y guarda el inventario en archivo.
* `cargarDatos()` → recupera la información guardada.

```java
package retrogaming;

import java.io.*;
import java.util.ArrayList;

public class Inventario implements Serializable {

    private ArrayList<Videojuego> videojuegos;

    public Inventario() {
        videojuegos = new ArrayList<>();
    }

    public void agregarVideojuego(Videojuego juego) {
        videojuegos.add(juego);
        System.out.println("Juego agregado: " + juego.getTitulo());
    }

    public void listarInventario() {
        if (videojuegos.isEmpty()) {
            System.out.println("El inventario está vacío.");
            return;
        }

        System.out.println("\n=== INVENTARIO ===");
        for (Videojuego juego : videojuegos) {
            juego.mostrarInformacion();
        }
    }

    public void guardarDatos(String nombreArchivo) {
        try {
            ObjectOutputStream archivo = new ObjectOutputStream(new FileOutputStream(nombreArchivo));
            archivo.writeObject(videojuegos);
            archivo.close();
            System.out.println("Inventario guardado correctamente!");
        } catch (IOException e) {
            System.out.println("Error al guardar: " + e.getMessage());
        }
    }

    public void cargarDatos(String nombreArchivo) {
        try {
            ObjectInputStream archivo = new ObjectInputStream(new FileInputStream(nombreArchivo));
            videojuegos = (ArrayList<Videojuego>) archivo.readObject();
            archivo.close();
            System.out.println("Inventario cargado correctamente.");
        } catch (IOException | ClassNotFoundException e) {
            System.out.println("Error al cargar: " + e.getMessage());
        }
    }
}
```
---

# 4. Implementación de Serialización

Se utilizó la interfaz `Serializable` de Java para permitir que los objetos puedan convertirse en bytes y almacenarse en un archivo.

## Guardado de datos

Se utilizó `ObjectOutputStream` para escribir el objeto en el archivo:

```text
inventario.dat
```

## Carga de datos

Se utilizó `ObjectInputStream` para reconstruir los objetos desde el archivo.

---

# 5. Ejecución del programa
1. Crear un objeto `Inventario`.
2. Crear tres videojuegos:
   * Pac-Man (Nintendo Switch, 1990)
   * Gatos y Sopa (NEOWIS, 2021)
   * Barbie DreamHouse Adventures (iOS, 2018)
3. Agregarlos al inventario.
4. Mostrar inventario inicial.
5. Guardar datos en `inventario.dat`.
6. Simular reinicio creando un nuevo inventario vacío.
7. Cargar datos desde `inventario.dat`.
8. Mostrar inventario recuperado.
---

# 6. Evidencias de ejecución

## Captura 1: Inventario inicial

*(Insertar captura aquí)*

---

## Captura 2: Guardado exitoso

*(Insertar captura aquí)*

---

## Captura 3: Carga exitosa del archivo

*(Insertar captura aquí)*

---

# Archivo generado

`inventario.dat`
