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

![Biblioteca](./Biblio.drawio.png)

### 2. Sistema de tienda online
| Elemento | Descripción |
| :--- | :--- |
| **ID** | TO01 |
| **Caso de uso** | Realizar compra de productos en línea |
| **Actores** | Cliente, Sistema de Inventario, Pasarela de Pagos |
| **Propósito** | Permitir al cliente seleccionar productos y finalizar la compra mediante un pago seguro. |
| **Descripción** | 1. El Cliente selecciona productos y los **Agrega al carrito**. <br> 2. El Cliente inicia el proceso de **Pagar**. <br> 3. El Sistema solicita los datos de facturación y envío. <br> 4. El Cliente confirma el monto y procesa la transacción. <br> 5. El Sistema confirma la compra y actualiza el inventario. |
| **Precondiciones** | El cliente ha iniciado sesión en su cuenta. <br> Los productos seleccionados tienen stock disponible. <br> El sistema de pagos está operativo. |
| **Postcondiciones** | La venta queda registrada en el sistema. <br> Se genera un comprobante de pago para el cliente. <br> El carrito de compras se vacía tras el éxito de la operación. |
| **Extensiones síncronas** | **Si el cliente desea Aplicar descuento:** El sistema valida el código antes de procesar el pago final. <br> **Si el pago es rechazado:** El sistema solicita un nuevo método de pago. <br> **Si el stock se agota durante el proceso:** El sistema notifica al cliente y actualiza el carrito. |



### 3. Sistema de chat

| Elemento | Descripción |
| :--- | :--- |
| **ID** | CH02 |
| **Caso de uso** | Gestionar intercambio de mensajes en tiempo real |
| **Actores** | Usuario Emisor, Usuario Receptor, Servidor de Chat, Servicio de Notificaciones |
| **Propósito** | Permitir la comunicación bidireccional entre usuarios mediante el envío y recepción de mensajes con alertas inmediatas. |
| **Descripción** | 1. El Usuario **Inicia sesión** en la aplicación. <br> 2. El Usuario Emisor redacta y ejecuta la acción de **Enviar mensaje**. <br> 3. El Servidor de Chat procesa el mensaje y lo entrega al destinatario. <br> 4. El Usuario Receptor procede a **Recibir mensaje**. <br> 5. El Sistema actualiza el estado del mensaje (enviado/recibido/leído). |
| **Precondiciones** | El usuario tiene una conexión a internet activa. <br> El usuario se ha autenticado correctamente. <br> El destinatario está en la lista de contactos del emisor. |
| **Postcondiciones** | El mensaje se almacena en el historial de chat de ambos usuarios. <br> El receptor visualiza el contenido del mensaje. <br> Se confirma la entrega al emisor. |
| **Extensiones síncronas** | **Si se requiere Incluir notificaciones:** El sistema genera una alerta visual/sonora en el dispositivo del receptor al detectar un mensaje nuevo. <br> **Si el inicio de sesión falla:** El sistema solicita verificar credenciales. <br> **Si el mensaje no se puede enviar:** El sistema muestra un icono de error y permite reintentar. |

### 4. Sistema de reservas de hotel

| Elemento | Descripción |
| :--- | :--- |
| **ID** | RH03 |
| **Caso de uso** | Gestionar reservas de habitaciones |
| **Actores** | Cliente, Recepcionista |
| **Propósito** | Permitir la gestión integral de alojamiento, desde la búsqueda hasta la gestión de cancelaciones y disponibilidad. |
| **Descripción** | 1. El Cliente procede a **Buscar habitación** por fechas. <br> 2. El Cliente selecciona la opción de **Reservar**. <br> 3. El Sistema solicita datos del cliente y garantía de pago. <br> 4. El Recepcionista valida la reserva en el sistema. <br> 5. El Cliente puede **Cancelar** su reserva si es necesario. |
| **Precondiciones** | El sistema de gestión hotelera está en línea. <br> Existe inventario de habitaciones cargado. <br> El Cliente cuenta con un método de contacto válido. |
| **Postcondiciones** | La disponibilidad de la habitación se actualiza en tiempo real. <br> Se emite una confirmación de reserva o cancelación. |
| **Extensiones sincrónicas** | **Si no hay disponibilidad:** El sistema ofrece fechas alternativas o tipos de habitación distintos. <br> **Si el Cliente desea Cancelar:** El sistema verifica si aplica penalización según la fecha. <br> **Si la garantía de pago falla:** La reserva queda en estado "pendiente" por tiempo limitado. |

### 5. Sistema Académico

