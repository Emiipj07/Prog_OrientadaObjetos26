## Problema 1: Modelado de sistema de crédito en tienda de electrodomésticos

### Planteamiento

Un negocio de venta de electrodomésticos decidió implementar y otorgar una línea de crédito a sus clientes para la compra de productos.

Los créditos son solicitados por los clientes al vendedor al momento de realizar la compra y deben ser autorizados por un representante de la gerencia de créditos.  
El pago se realiza mediante débito automático en tarjetas de crédito.

Si el crédito se acepta, el producto se entrega al cliente de forma inmediata.

Cada mes se cobrará automáticamente el pago de las cuotas en la tarjeta del cliente.

Se desea modelar el proceso de:
- Solicitud de crédito  
- Otorgamiento de crédito  
- Pago del crédito  

### Indicaciones

- Represente todo el proceso completo como un único caso de uso, mencionando sus pasos principales, sin detallar alternativas.  

- Identifique los distintos actores que intervienen en el proceso.  

- Identifique casos de uso derivados del proceso principal.  

- Identifique nuevos casos de uso considerando variaciones, casos previos, posteriores o alternativos.  

- Identifique casos de uso reutilizables que puedan ser incluidos en otros casos.

## Caso de uso: Gestionar crédito

| Elemento | Descripción |
|----------|-------------|
| ID | V-01 |
| Caso de uso | Gestionar crédito para compra |
| Actores | Cliente, Vendedor, Representante de créditos, Sistema bancario |
| Propósito | Permitir solicitar, aprobar y pagar un crédito para comprar productos |
| Descripción | 1. El cliente selecciona producto.<br>2. Solicita crédito al vendedor.<br>3. El vendedor registra la solicitud.<br>4. Se envía al representante.<br>5. Se evalúa el crédito.<br>6. Se aprueba el crédito.<br>7. Se registra en el sistema.<br>8. Se configura débito automático.<br>9. Se autoriza entrega.<br>10. Se entrega producto.<br>11. Se cobran cuotas mensuales automáticamente. |
| Precondiciones | - Sistema activo<br>- Cliente con tarjeta válida<br>- Producto disponible |
| Postcondiciones | - Crédito aprobado<br>- Producto entregado<br>- Pagos configurados |
| Extensiones síncronas | - No se apueba el crédito. <br>- El cliente no está registrado. |

## Problema 2: Modelado de diagrama de casos de uso de una cadena de videoclubes

### Planteamiento

La famosa cadena de videoclubes “Los Bloques de Búster” nos ha contratado con el fin de desarrollar un sistema para sistematizar sus locales.

Hasta el día de hoy se han mantenido una serie de reuniones con el cliente con el fin de determinar los requerimientos del sistema. De tales reuniones, se ha determinado lo siguiente:

- El sistema deberá permitir que los clientes consulten el catálogo de películas.  
  A partir del mismo, una vez seleccionada una película, se deberá poder acceder a la información de la misma como ser su clasificación, su género y un breve resumen.  
  Asimismo, opcionalmente, se deberá poder consultar la disponibilidad del video.

- Los empleados del videoclub deberán poder, a través del sistema, registrar las rentas y devoluciones por parte de los clientes, y consultar, dado un cliente, los videos que éste posea en renta.  
  Si registrando una renta, resulta que el cliente no se encuentra registrado, el sistema deberá permitir que se efectúe su alta.

- El sistema deberá generar automáticamente un informe todas las mañanas a las 9:00 a.m. que muestre todos los clientes que se encuentran atrasados con sus devoluciones.

## Caso de uso: Registrar renta de película

| Elemento | Descripción |
|----------|-------------|
| ID | BB-02 |
| Caso de uso | Registrar renta de película |
| Actores | Empleado |
| Propósito | Permitir registrar el préstamo de una película a un cliente |
| Descripción | 1. El sistema solicita el ID del cliente.<br>2. El empleado ingresa los datos.<br>3. El sistema verifica si el cliente existe.<br>4. Si no existe, se solicita su registro.<br>5. El empleado registra al cliente.<br>6. El sistema muestra el catálogo.<br>7. El empleado selecciona la película.<br>8. El sistema verifica disponibilidad.<br>9. El empleado confirma la renta.<br>10. El sistema registra la renta.<br>11. Se actualiza el stock.<br>12. Se muestra confirmación. |
| Precondiciones | - Sistema operativo<br>- Catálogo disponible<br>- Empleado autenticado |
| Postcondiciones | - Renta registrada<br>- Película no disponible |
| Extensiones síncronas | - Cliente no registrado → registrar cliente<br>- Película no disponible → mostrar mensaje<br>- Cancelación → finalizar proceso |

![Caso de uso2](./Pelicula.png)

## Problema 3: Modelado de máquina expendedora de bebidas

### Planteamiento

Se ha decidido fabricar una máquina para la expedición y venta de bebidas en forma automática.

El cliente selecciona algunos de los productos ofrecidos, uno o más, por medio de la pulsación de botones.  
Los artículos pueden ser de distintos tipos: latas de refresco, jugos o botellas.

Solamente se puede solicitar un tipo de producto a la vez.  
La máquina reconoce el pedido del cliente.  
Si no hay en existencia, le indica al cliente por medio de un mensaje.

La máquina acepta las monedas del cliente, reconociendo distintos tipos.  
Si las monedas no cubren el total del importe, las devuelve y le avisa al cliente mediante un mensaje.  
En caso contrario, libera las bebidas solicitadas, actualiza el stock de productos e imprime un ticket.

El encargado de la reposición repone los artículos de acuerdo a lo indicado en la pantalla.  
Para ello, accede mediante una contraseña a una interfaz propia.

Al realizar la reposición:
- Debe indicar el producto  
- Debe indicar la cantidad repuesta  

El sistema:
- Actualiza el stock  
- Emite un resumen de faltantes  
- Imprime dos copias (constancia y factura)

## Caso de uso: Comprar bebida

| Elemento | Descripción |
|----------|-------------|
| ID | MACH-03 |
| Caso de uso | Comprar bebida |
| Actores | Cliente |
| Propósito | Permitir al cliente comprar una bebida automáticamente |
| Descripción | Flujo principal:<br>1. El cliente selecciona una bebida.<br>2. El sistema registra la selección.<br>3. Se verifica disponibilidad.<br>4. Se solicita el pago.<br>5. El cliente introduce monedas.<br>6. El sistema valida las monedas.<br>7. Se calcula el total.<br>8. Si es suficiente, se procesa la compra.<br>9. Se entrega el producto.<br>10. Se actualiza el stock.<br>11. Se imprime ticket. |
| Precondiciones | - Máquina encendida<br>- Producto disponible |
| Postcondiciones | - Producto entregado<br>- Stock actualizado<br>- Ticket generado |
| Extensiones síncronas | - Sin stock → mensaje<br>- Pago insuficiente → devolución<br>- Moneda inválida → rechazo |

## Caso de uso: Reponer productos

| Elemento | Descripción |
|----------|-------------|
| ID | MACH-03 |
| Caso de uso | Reponer productos |
| Actores | Encargado |
| Propósito | Permitir la reposición de productos en la máquina |
| Descripción | 1. El encargado inicia sesión con contraseña.<br>2. El sistema valida acceso.<br>3. Se muestran productos con bajo stock.<br>4. Se selecciona producto.<br>5. Se ingresa cantidad.<br>6. Se actualiza stock.<br>7. Se genera reporte.<br>8. Se imprimen copias. |
| Precondiciones | - Encargado autorizado<br>- Sistema activo |
| Postcondiciones | - Stock actualizado<br>- Reporte generado |
| Extensiones síncronas | - Contraseña incorrecta → acceso denegado<br>- Error en datos → solicitar nuevamente |

![Caso de uso 3](./Bebidas.png)
