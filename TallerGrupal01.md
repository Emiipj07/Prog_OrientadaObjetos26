# Taller Grupal - Casos de uso
## Integrantes: Jhostin Molina, Emilia Peña y Fabio Tapia
### 1. Sistema de biblioteca

## Caso de uso: Prestar libro

| Elemento | Descripción |
|----------|-------------|
| ID | BIB-01 |
| Caso de uso | Prestar libro |
| Actores | Bibliotecario, Usuario |
| Propósito | Permitir registrar el préstamo de un libro a un usuario |
| Descripción | 1. El bibliotecario ingresa el ID del usuario.<br>2. El sistema verifica si el usuario está registrado.<br>3. El bibliotecario selecciona el libro.<br>4. El sistema verifica la disponibilidad del libro.<br>5. El sistema registra el préstamo.<br>6. El sistema actualiza el estado del libro.<br>7. El sistema muestra confirmación del préstamo. |
| Precondiciones | - Usuario registrado<br>- Libro existente en el sistema |
| Postcondiciones | - Préstamo registrado<br>- Libro marcado como no disponible |
| Extensiones síncronas | - Usuario no registrado → registrar usuario<br>- Libro no disponible → mostrar mensaje |

