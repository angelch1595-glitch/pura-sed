# Requisitos funcionales, no funcionales e historias de usuario

## 2. Especificar los Requisitos Funcionales y No Funcionales

### Requisitos funcionales

| ID | Requisito | Descripción | Historias |
|---|---|---|---|
| RF-01 | Acceso del cliente  | El sistema permite el acceso del cliente sin registro mediante permiso del Asistente, sele activa la mesa perteneciente a su reserva. | HU-01 |
| RF-02 | Autenticación y roles | El sistema autentica al personal y restringe las funciones según su rol. | HU-02, HU-03 |
| RF-03 | Bitácora (time line) | El sistema registra y permite consultar las acciones realizadas. | HU-04 |
| RF-04 | Catálogo de menú | El sistema muestra el menú, los combos, las variantes y los espectáculos. | HU-05 a HU-07, HU-09 |
| RF-05 | Promociones | El sistema permite crear promociones por porcentaje con vigencia temporal. | HU-08 |
| RF-06 | Disponibilidad de productos | El sistema sombrea los productos agotados al cliente y los resalta al personal. | HU-10 |
| RF-07 | Inventario | El sistema permite registrar ingresos y descuenta el stock con cada pedido. | HU-11, HU-12 |
| RF-08 | Registro de pedidos | El cliente registra pedidos por mesa desde la Tablet de su mesa. | HU-13 |
| RF-09 | Distribución de pedidos | El sistema envía cada producto a cocina o bar. | HU-14, HU-15 |
| RF-10 | Seguimiento de pedidos | El cliente puede ver el proceso de su pedido. | HU-16 |
| RF-11 | Reservas | El sistema permite reservar, modificar, cancelar y visualizar reservas. | HU-17 a HU-19 |
| RF-12 | Pagos | El sistema habilita el cobro y registra pagos con tarjeta, transferencia o efectivo. | HU-20 a HU-23 |
| RF-13 | Facturación | El sistema genera una factura por cada pago confirmado (orden de compra). | HU-24 |
| RF-14 | Satisfacción | El sistema recoge la calificación del mesero y del servicio. | HU-25, HU-26 |
| RF-15 | Reportes | El sistema presenta reportes y gráficos actualizados por jornada. | HU-27 a HU-31 |
| RF-16 | Exportación | El sistema exporta los reportes a Excel, con una hoja por tópico. | HU-32 |

### Requisitos no funcionales

| ID | Categoría | Requisito |
|---|---|---|
| RNF-01 | Seguridad | El sistema debe tener un alto nivel de seguridad, porque desde él se gestionan usuarios, pagos y administración. |
| RNF-02 | Seguridad | Las contraseñas y los números de serie de las tarjetas deben almacenarse cifrados (no almacenarse en el caso de tarjetas). |
| RNF-03 | Seguridad | Toda comunicación debe realizarse por HTTPS, y la API debe validar el rol del usuario en cada petición. |
| RNF-04 | Auditoría | La bitácora debe ser de solo lectura y conservar las acciones del personal. |
| RNF-05 | Disponibilidad | El sistema debe estar en la nube y disponible en los horarios de mayor uso: clientes de 7 pm a 2 am y administración desde las 5 pm. Disponibilidad mínima del 99 % en ese horario (propuesto). |
| RNF-06 | Rendimiento | Las operaciones habituales deben responder en menos de 3 segundos (propuesto). Los pedidos, estados y reportes deben actualizarse de inmediato. |
| RNF-07 | Concurrencia | El sistema debe soportar el uso simultáneo de clientes, meseros y administradores en el horario pico. |
| RNF-08 | Usabilidad | La interfaz debe ser muy intuitiva para usuarios no técnicos. La del cliente, visual y atractiva; la administrativa, eficiente y sin saturación. |
| RNF-09 | Compatibilidad | El diseño debe ser responsivo: ctablets para clientes y meseros; PC y tablets para la administración; navegadores modernos. |
| RNF-10 | Acceso remoto | El superadministrador deben poder acceder de forma remota, porque no forman parte del personal del bar. |
| RNF-11 | Integridad | El sistema no debe permitir reservas duplicadas, pagos duplicados ni inventario negativo. |
| RNF-12 | Mantenibilidad | El sistema debe separar el backend (ASP.NET Core Web API) del frontend (Blazor WebAssembly), documentar la API con Swagger y versionar el código con Git. |
| RNF-13 | Respaldo | La base de datos debe contar con copias de seguridad periódicas (propuesto). |

a.	Documentar los requerimientos utilizando User Stories.

i.	Ejemplo de User Story: Como cliente, quiero ver los combos ofrecidos en el bar en un catálogo para poder hacer un pedido.

b.	Definir los criterios de aceptación para cada historia.

## Acceso y seguridad

### HU-01 · Acceso del cliente mediante código QR

| Campo | Contenido |
|---|---|
| Historia | Como cliente, quiero acceder al menú del bar a mi mesa que se activa al reservar o al ingresar al local, para consultar el menú y el seguimiento de mi pedido sin tener que registrarme. |
| Prioridad | Alta |
| Criterios de aceptación | •	La mesa se activa únicamente cuando se confirma una reserva o se registra el ingreso del cliente al local.<br>•	Una mesa no activado o vencido muestra un mensaje informativo y no da acceso al menú.<br>•	El cliente accede al menú y al seguimiento de su pedido sin crear cuenta ni ingresar contraseña.<br>•	El acceso queda asociado a una mesa o sesión, de modo que los pedidos y el pago se vinculen a ella, únicamente para ese cliente y disponible mientras este asociada la reserva.<br>•	El menú también es accesible desde el equipo disponible en el local. |

### HU-02 · Inicio de sesión del personal

| Campo | Contenido |
|---|---|
| Historia | Como miembro del personal (mesero, administrador de cocina, administrador de bar, asistente, administrador o superadministrador), quiero iniciar sesión con mis credenciales, para acceder únicamente a las funciones de mi rol. |
| Prioridad | Alta |
| Criterios de aceptación | •	Con credenciales válidas, el sistema redirige a la vista correspondiente al rol del usuario.<br>•	Con credenciales inválidas, se muestra un mensaje de error genérico sin indicar cuál dato falló.<br>•	Las opciones no autorizadas para el rol no se muestran, y el acceso directo por URL o API devuelve “acceso denegado”.<br>•	Las contraseñas se almacenan cifradas (hash), nunca en texto plano.<br>•	La sesión expira tras un periodo de inactividad (tiempo a definir con el Product Owner). |

### HU-03 · Gestión de usuarios y roles

| Campo | Contenido |
|---|---|
| Historia | Como superadministrador, quiero crear, modificar y desactivar usuarios del personal y asignarles un rol, para controlar quién accede al sistema y qué puede hacer. |
| Prioridad | Alta |
| Criterios de aceptación | •	Solo el superadministrador puede acceder a este módulo.<br>•	Para crear un usuario se exige nombre, usuario o correo, contraseña inicial y rol.<br>•	Un usuario desactivado no puede iniciar sesión, pero su historial de acciones se conserva.<br>•	Los cambios de rol se aplican en el siguiente inicio de sesión del usuario afectado.<br>•	Cada alta, modificación o desactivación queda registrada en la bitácora. |

### HU-04 · Consulta de bitácora de acciones

| Campo | Contenido |
|---|---|
| Historia | Como administrador, quiero consultar un registro de las acciones realizadas en el sistema, para auditar la operación del bar y detectar irregularidades. |
| Prioridad | Media |
| Criterios de aceptación | •	Cada registro incluye usuario, acción realizada, módulo afectado y fecha y hora.<br>•	Se registran las acciones del personal (pedidos, pagos, inventario, promociones, reservas y gestión de usuarios).<br>•	Las acciones de los clientes se registran solo si estos decidieron registrarse voluntariamente.<br>•	La bitácora es de solo lectura: ningún usuario puede editar ni eliminar registros.<br>•	Se puede filtrar por usuario, rango de fechas y tipo de acción. |

## Menú, promociones y espectáculos

### HU-05 · Consultar el menú por categorías

| Campo | Contenido |
|---|---|
| Historia | Como cliente, quiero ver el menú organizado por categorías (comida, bebidas, promociones y espectáculo), para encontrar fácilmente lo que deseo consumir. |
| Prioridad | Alta |
| Criterios de aceptación | •	El menú muestra las categorías definidas y, por producto, nombre, descripción, imagen y precio.<br>•	Si el producto tiene una promoción vigente, se muestra el precio original y el precio con descuento.<br>•	Los productos agotados no se muestran al cliente (ver HU-10).<br>•	La interfaz es visual, atractiva y se adapta correctamente a pantallas de celular.<br>•	El menú base es fijo: solo cambian precios por promociones y la disponibilidad. |

### HU-06 · Ver combos y promociones en un catálogo

| Campo | Contenido |
|---|---|
| Historia | Como cliente, quiero ver los combos ofrecidos en el bar en un catálogo, para poder elegirlos y solicitarlos en mi pedido. |
| Prioridad | Alta |
| Criterios de aceptación | •	El catálogo lista solo los combos vigentes, con nombre, productos incluidos y precio.<br>•	Los combos con descuento muestran el precio anterior tachado y el precio final.<br>•	Los combos que incluyan un producto agotado no se muestran al cliente.<br>•	El catálogo se obtiene del backend mediante el endpoint GET /api/combos (entregable del Sprint 1).<br>•	Si no hay combos disponibles, se muestra un mensaje informativo. |

### HU-07 · Ver variantes e ingredientes de un producto

| Campo | Contenido |
|---|---|
| Historia | Como cliente, quiero ver las variantes e ingredientes disponibles de cada producto, para saber cómo puedo pedirlo según mis preferencias. |
| Prioridad | Media |
| Criterios de aceptación | •	Los productos con variantes (p. ej. tipos de bebida) las muestran en su detalle.<br>•	Los productos con ingredientes personalizables listan los ingredientes que se pueden incluir o excluir.<br>•	Solo se muestran variantes e ingredientes disponibles en el inventario.<br>•	Las variantes que alteran el precio muestran el precio actualizado. |

### HU-08 · Gestionar promociones por porcentaje

| Campo | Contenido |
|---|---|
| Historia | Como administrador, quiero crear promociones con un porcentaje de descuento y vigencia temporal sobre productos o combos, para ofrecer descuentos sin modificar el menú base. |
| Prioridad | Alta |
| Criterios de aceptación | •	Se define el producto o combo, el porcentaje de descuento y las fechas y horas de inicio y fin.<br>•	No se permite un porcentaje fuera del rango válido (mayor a 0 y menor a 100) ni una fecha de fin anterior a la de inicio.<br>•	Mientras la promoción está vigente, el menú del cliente muestra el precio con descuento; al vencer, vuelve al precio base automáticamente.<br>•	El precio base del producto nunca se modifica de forma permanente.<br>•	La promoción puede editarse o desactivarse antes de su vencimiento. |

### HU-09 · Gestionar espectáculos

| Campo | Contenido |
|---|---|
| Historia | Como administrador, quiero registrar los espectáculos del bar (nombre, descripción, fecha y horario), para que los clientes los vean en el menú. |
| Prioridad | Media |
| Criterios de aceptación | •	Se puede crear, editar y desactivar un espectáculo con nombre, descripción, fecha y horario.<br>•	Los espectáculos activos aparecen en la categoría “Espectáculo” del menú del cliente.<br>•	Los espectáculos con fecha pasada dejan de mostrarse al cliente.<br>•	La información del espectáculo se usa en el reporte de permanencia de clientes (HU-31). |

### HU-10 · Ocultar productos agotados al cliente

| Campo | Contenido |
|---|---|
| Historia | Como administrador de cocina o de bar, quiero que los productos agotados se oculten al cliente y se muestren sombreados al personal, para evitar pedidos de productos no disponibles sin perder visibilidad del inventario. |
| Prioridad | Alta |
| Criterios de aceptación | •	Cuando el stock llega a cero (o se marca manualmente como agotado), el producto desaparece del menú del cliente.<br>•	En las vistas del personal, el producto se muestra sombreado y con la etiqueta “Agotado”.<br>•	El mesero no puede agregar un producto agotado a un pedido.<br>•	Al reponerse el stock, el producto vuelve a mostrarse automáticamente al cliente. |

## Inventario

### HU-11 · Registrar ingreso de productos al inventario

| Campo | Contenido |
|---|---|
| Historia | Como administrador de cocina o de bar, quiero registrar el ingreso de nuevos productos e insumos al inventario de mi área, para mantener el stock actualizado. |
| Prioridad | Alta |
| Criterios de aceptación | •	Cada administrador ve y modifica únicamente el inventario de su área (cocina o bar).<br>•	El registro exige nombre del producto, categoría, cantidad, unidad de medida y fecha de ingreso.<br>•	El stock se actualiza de inmediato tras guardar el registro.<br>•	Se rechazan cantidades negativas, vacías o no numéricas.<br>•	Cada movimiento de inventario queda registrado en la bitácora. |

### HU-12 · Descuento automático de inventario por pedido

| Campo | Contenido |
|---|---|
| Historia | Como administrador de cocina o de bar, quiero que el inventario se descuente automáticamente al confirmarse un pedido, para no tener que registrar manualmente cada consumo. |
| Prioridad | Media |
| Criterios de aceptación | •	Al confirmar un pedido, se descuenta del stock la cantidad de cada producto o insumo utilizado.<br>•	Si un pedido se cancela antes de prepararse, el stock descontado se restituye.<br>•	Cuando el stock llega a cero, se activa el comportamiento de producto agotado (HU-10).<br>•	El stock nunca puede quedar en valores negativos. |

## Pedidos

### HU-13 · Registrar pedido por mesa desde el celular

| Campo | Contenido |
|---|---|
| Historia | Como cliente, quiero registrar desde mi Tablet de la mesa los productos que solicita, incluyendo variantes, para evitar las anotaciones en papel y reducir errores en los pedidos. |
| Prioridad | Alta |
| Criterios de aceptación | •	Se selecciona la mesa y se agregan productos con cantidad, variante, ingredientes y observaciones.<br>•	Solo se pueden agregar productos disponibles (no agotados).<br>•	Al confirmar, el pedido queda identificado con número, mesa, fecha y hora.<br>•	Se pueden agregar nuevos productos a una mesa que ya tiene una cuenta abierta.<br>•	Solo los clientes pueden registrar pedidos; el flujo funciona desde el navegador de la Tablet. |

### HU-14 · Distribución automática del pedido a cocina y bar

| Campo | Contenido |
|---|---|
| Historia | Como cliente, quiero que el sistema envíe automáticamente cada producto del pedido a cocina o a bar según corresponda, para el mesero no tener que desplazarme a estas áreas. |
| Prioridad | Alta |
| Criterios de aceptación | •	Cada producto está asociado a un área de preparación (cocina o bar).<br>•	Un pedido mixto se divide automáticamente y cada área recibe únicamente sus productos.<br>•	El pedido llega a cada área de forma inmediata, sin recargar la pantalla manualmente.<br>•	El mesero no necesita intervenir en el envío una vez confirmado el pedido. |

### HU-15 · Gestionar los pedidos de mi área

| Campo | Contenido |
|---|---|
| Historia | Como administrador de cocina o de bar, quiero ver los pedidos de mi área y actualizar su estado, para organizar la preparación y avisar cuando estén listos. |
| Prioridad | Alta |
| Criterios de aceptación | •	La lista muestra mesa, productos, variantes, observaciones y hora del pedido, ordenados del más antiguo al más reciente.<br>•	El estado puede cambiarse en orden: pendiente → en preparación → listo.<br>•	El cambio de estado es visible de inmediato para el mesero y para el cliente.<br>•	Cada administrador solo ve los pedidos de su propia área. |

### HU-16 · Seguimiento del pedido por el cliente

| Campo | Contenido |
|---|---|
| Historia | Como cliente, quiero ver el estado de mi pedido en tiempo real, para saber cuánto falta para recibirlo. |
| Prioridad | Media |
| Criterios de aceptación | •	El cliente ve los productos de su pedido con su estado actual (pendiente, en preparación o listo).<br>•	El estado se actualiza sin que el cliente tenga que recargar la página.<br>•	El cliente solo puede ver los pedidos de su mesa o sesión.<br>•	El seguimiento está disponible desde el celular y desde el equipo del local. |

## Reservas

### HU-17 · Reservar una mesa en línea

| Campo | Contenido |
|---|---|
| Historia | Como cliente, quiero reservar una mesa indicando fecha, hora y número de personas, para asegurar mi lugar sin tener que llamar por teléfono. |
| Prioridad | Alta |
| Criterios de aceptación | •	El formulario solicita nombre, contacto, fecha, hora y número de personas.<br>•	El sistema valida la disponibilidad y no permite reservas duplicadas para la misma mesa y horario.<br>•	No se aceptan fechas pasadas ni horarios fuera del funcionamiento del bar.<br>•	Al confirmar, se muestra un código de reserva y se activa el QR de acceso (HU-01). |

### HU-18 · Gestionar reservas (asistente)

| Campo | Contenido |
|---|---|
| Historia | Como asistente, quiero registrar, modificar y cancelar reservas, incluidas las solicitadas por teléfono, para reemplazar la hoja de cálculo manual. |
| Prioridad | Alta |
| Criterios de aceptación | •	La asistente puede crear una reserva telefónica con los mismos datos que una reserva en línea.<br>•	Puede modificar fecha, hora o personas, y cancelar una reserva; al cancelar, la mesa queda libre.<br>•	Existe una agenda por fecha con todas las reservas y su estado.<br>•	Cada cambio queda registrado en la bitácora. |

### HU-19 · Visualizar las reservas del negocio

| Campo | Contenido |
|---|---|
| Historia | Como administrador, quiero ver las reservas del día y de fechas futuras, para anticipar la ocupación del local. |
| Prioridad | Media |
| Criterios de aceptación | •	La vista muestra las reservas con fecha, hora, mesa, número de personas y estado.<br>•	Se puede filtrar por fecha y por estado (confirmada, cancelada, cumplida).<br>•	La vista es de consulta y refleja los cambios de la asistente de inmediato. |

## Pagos y facturación

### HU-20 · Habilitar el cobro de una cuenta

| Campo | Contenido |
|---|---|
| Historia | Como administrador, quiero habilitar el pago de la cuenta de una mesa, para que el cliente pueda pagar el total únicamente cuando el consumo esté cerrado y verificado. |
| Prioridad | Alta |
| Criterios de aceptación | •	Mientras el pago no esté habilitado, el cliente no puede pagar.<br>•	Al habilitarlo, el cliente ve el detalle del consumo, los descuentos aplicados y el total a pagar.<br>•	El pago corresponde al total de la cuenta de la mesa.<br>•	La habilitación queda registrada en la bitácora. |

### HU-21 · Pagar con tarjeta

| Campo | Contenido |
|---|---|
| Historia | Como cliente, quiero pagar mi cuenta con tarjeta desde la plataforma, ingresando el número de serie y el código de confirmación de 4 dígitos, para pagar sin esperar al mesero. |
| Prioridad | Alta |
| Criterios de aceptación | •	La opción de tarjeta solo está disponible cuando el pago fue habilitado (HU-20).<br>•	El sistema valida el formato del número de serie y del código de 4 dígitos antes de procesar.<br>•	Si el pago es exitoso, la cuenta pasa a “pagada” y se muestra la confirmación.<br>•	Si falla, se muestra un mensaje de error y la cuenta permanece pendiente.<br>•	El número de serie se almacena cifrado y nunca se muestra completo en pantalla. |

### HU-22 · Pagar por transferencia con comprobante

| Campo | Contenido |
|---|---|
| Historia | Como cliente, quiero pagar por transferencia y subir el comprobante, para registrar mi pago sin necesidad de acercarme a caja. |
| Prioridad | Alta |
| Criterios de aceptación | •	Se muestran los datos de la cuenta bancaria del bar y el monto exacto a transferir.<br>•	El cliente puede subir el comprobante en un formato permitido (imagen o PDF) y con un tamaño máximo definido.<br>•	El pago queda en estado “pendiente de verificación” hasta que el personal autorizado lo confirme.<br>•	Una vez confirmado, la cuenta pasa a “pagada”. |

### HU-23 · Pagar en efectivo

| Campo | Contenido |
|---|---|
| Historia | Como cliente, quiero seleccionar el pago en efectivo, para cancelar mi cuenta directamente en el local. |
| Prioridad | Media |
| Criterios de aceptación | •	El cliente puede elegir “efectivo” como forma de pago cuando el cobro está habilitado.<br>•	La cuenta queda en estado “pago en efectivo por confirmar” hasta que el personal confirme la recepción del dinero.<br>•	Solo el personal autorizado puede confirmar el pago en efectivo.<br>•	Al confirmarse, la cuenta pasa a “pagada” y se genera la factura. |

### HU-24 · Generar factura

| Campo | Contenido |
|---|---|
| Historia | Como cliente, quiero recibir una factura al completar mi pago, para contar con el comprobante de mi consumo. |
| Prioridad | Alta |
| Criterios de aceptación | •	La factura se genera automáticamente cuando el pago pasa a estado confirmado.<br>•	Incluye número único y secuencial, fecha, datos del cliente, detalle de productos, descuentos, total y forma de pago.<br>•	El cliente puede visualizarla y descargarla desde la plataforma.<br>•	Antes de emitirla, el sistema solicita los datos de facturación del cliente. |

## Satisfacción del cliente

### HU-25 · Calificar al mesero

| Campo | Contenido |
|---|---|
| Historia | Como cliente, quiero calificar al mesero que me atendió con una a cinco estrellas, para expresar mi satisfacción con la atención recibida. |
| Prioridad | Media |
| Criterios de aceptación | •	La calificación se presenta automáticamente después de registrarse el pago.<br>•	La escala va de 1 (mínimo) a 5 estrellas (máximo) y es necesario elegir un valor para enviarla.<br>•	La calificación queda asociada al mesero que atendió la mesa.<br>•	Solo se permite una calificación por cuenta. |

### HU-26 · Calificar el servicio general

| Campo | Contenido |
|---|---|
| Historia | Como cliente, quiero calificar mi experiencia general en el bar, para comunicar cómo me sentí en el lugar. |
| Prioridad | Media |
| Criterios de aceptación | •	La calificación general se presenta junto con la del mesero, después de registrarse el pago.<br>•	Se usa la misma escala de 1 a 5 estrellas.<br>•	Solo se permite una calificación por cuenta.<br>•	Los resultados alimentan el reporte de nivel de satisfacción (HU-29). |

## Reportes y estadísticas

### HU-27 · Reporte de ventas diarias

| Campo | Contenido |
|---|---|
| Historia | Como administrador o superadministrador, quiero ver las ventas diarias del bar, para conocer el rendimiento del negocio. |
| Prioridad | Alta |
| Criterios de aceptación | •	Muestra el total vendido y el número de cuentas pagadas por día, con filtro por rango de fechas.<br>•	Considera únicamente cuentas con pago confirmado.<br>•	Los datos se actualizan de inmediato, sin procesos manuales.<br>•	Los valores coinciden con las facturas emitidas. |

### HU-28 · Índice de pedidos por mesero

| Campo | Contenido |
|---|---|
| Historia | Como administrador o superadministrador, quiero ver el índice de pedidos atendidos por cada mesero, para evaluar su desempeño. |
| Prioridad | Media |
| Criterios de aceptación | •	Muestra por mesero la cantidad de pedidos y el monto vendido en el periodo elegido.<br>•	Permite filtrar por rango de fechas.<br>•	Los datos se actualizan de inmediato. |

### HU-29 · Nivel de satisfacción de los clientes

| Campo | Contenido |
|---|---|
| Historia | Como administrador o superadministrador, quiero ver el nivel de satisfacción de los clientes en un gráfico de pastel, para identificar la percepción del servicio. |
| Prioridad | Media |
| Criterios de aceptación | •	El gráfico de pastel muestra la distribución porcentual de calificaciones de 1 a 5 estrellas del servicio general.<br>•	Se muestra también el promedio de calificación por mesero.<br>•	Permite filtrar por rango de fechas.<br>•	Los datos se actualizan de inmediato. |

### HU-30 · Comparativo de ventas por día de la semana

| Campo | Contenido |
|---|---|
| Historia | Como administrador o superadministrador, quiero ver un gráfico de barras que compare las ventas según el día de la semana, para identificar los días de mayor y menor demanda. |
| Prioridad | Media |
| Criterios de aceptación | •	El gráfico muestra una barra por cada día, de lunes a domingo.<br>•	Los ejes están rotulados y el periodo analizado es seleccionable.<br>•	Los datos se actualizan de inmediato. |

### HU-31 · Índice de clientes que se quedan al espectáculo

| Campo | Contenido |
|---|---|
| Historia | Como administrador o superadministrador, quiero conocer el índice de clientes que permanecen durante el espectáculo, para evaluar su atractivo. |
| Prioridad | Baja |
| Criterios de aceptación | •	El índice se calcula como el porcentaje de clientes con cuenta activa durante el horario del espectáculo, sobre el total de clientes del día (fórmula a validar con el Product Owner).<br>•	Se puede consultar por espectáculo y por rango de fechas.<br>•	Los datos se actualizan de inmediato. |

### HU-32 · Exportar reportes a Excel

| Campo | Contenido |
|---|---|
| Historia | Como administrador o superadministrador, quiero exportar los reportes a un archivo de Excel, para conservarlos y analizarlos fuera del sistema. |
| Prioridad | Baja |
| Criterios de aceptación | •	El archivo .xlsx contiene una hoja por tópico: ventas diarias, pedidos por mesero, satisfacción, ventas por día de la semana y espectáculo.<br>•	Los datos exportados coinciden con los mostrados en pantalla.<br>•	La exportación es opcional: el resumen con gráficas ya está disponible en la plataforma. |

