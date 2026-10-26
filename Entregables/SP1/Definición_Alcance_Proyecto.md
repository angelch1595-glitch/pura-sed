# Definición del Proyecto y Alcance

Establecimiento del Product Backlog y los primeros requisitos funcionales.

## Actividades

1. **Definir los módulos principales del sistema:**

> a. Realiza preguntas guías a compañeros estudiantes y profesor para definir los módulos principales del sistema, como gestión de productos, ventas, usuarios, etc.

## a. Preguntas generales sobre el negocio

### i. ¿Cómo funciona actualmente la gestión del bar?

La gestión del bar es manual y no cuenta con ningún sistema informático:

- **Cobro:** sistema convencional, con pagos en efectivo, por transferencia o con tarjeta.

- **Menú:** menús físicos o un menú en Canva al que se accede mediante un código QR.

- **Reservas:** se solicitan por teléfono y se agendan manualmente en una hoja de cálculo.

- **Pedidos:** se registran en papelitos. El mesero toma el pedido en cada mesa y luego se desplaza al bar o a la cocina según corresponda.

- **Satisfacción del cliente:** la calificación se realiza de forma manual, en hojas el cliente registra una encuesta al finalizar su experiencia en el bar.

### ii. ¿Cuáles son los principales problemas que desea resolver con este sistema?

- Automatizar el cobro mediante un sistema de pago integrado.

- Ofrecer un menú interactivo y fácil de usar desde el celular.

- Contar con un sistema de reservas virtual, accesible para clientes y asistente, con vista para los administradores.

- Reducir la carga de trabajo de los meseros: registran el pedido en su celular y el sistema lo envía automáticamente al bar o a la cocina.

- Automatizar la encuesta de satisfacción, que se presenta al cliente tras el pago.

- Obtener información del negocio (ventas, productos más vendidos, desempeño) para decidir mejor.

### iii. ¿Qué procesos del bar considera que deberían ser automatizados?

- Registro de pedidos y su distribución a bar y cocina.

- Registro y confirmación de pagos, con emisión de factura.

- Registro de reservas.

- Descuento del inventario y aviso de productos agotados.

- Encuesta de satisfacción y generación de reportes.

### iv. ¿Quiénes serán los principales usuarios del sistema?

- **Cliente:** consulta el menú, ve el seguimiento de su pedido y puede realizar el pedido (ver y agregar su pedido (editar estableciendo una confirmación) pero una vez el pedido sale de cocina o bar no se puede eliminar), notificar el pago.

- **Mesero:** lleva los pedidos de las mesas.

- **Administrador de cocina:** gestiona el inventario y los pedidos de cocina.

- **Administrador de bar:** gestiona el inventario y los pedidos del bar.

- **Asistente:** gestiona las reservas de mesas.

- **Administrador:** gerente del bar. Supervisa pedidos, reservas, reportes, menú y promociones, además de que el administrador podrá gestionar el pago y habilitar la consulta de calificación.

- **Superadministrador:** equipo técnico. Tiene control total para el mantenimiento del sistema y accede de forma remota.

### v. ¿Tiene algún sistema previo que desea reemplazar o integrar?

No se cuenta con un sistema previo que tenga similitudes con el diseño que se desea realizar.

## b. Gestión de productos y menú

### i. ¿Qué tipo de productos ofrece el bar? (comida, bebidas, promociones, etc.)

- Comida

- Bebidas

- Combos y promociones

- Espectáculos

### ii. ¿Cada producto tiene variantes o ingredientes personalizables?

Sí. Los productos pueden tener variantes (por ejemplo, en las bebidas).

### iii. ¿Cómo desea gestionar el inventario de productos?

Cada administrador (cocina y bar) gestiona el inventario de su área: registra el ingreso de nuevos productos e insumos. El sistema descuenta el stock automáticamente con cada pedido y avisa cuando un producto llega a su nivel mínimo. (diariamente)

### iv. ¿Desea que el sistema permita crear o modificar el menú fácilmente?

Sí, de forma controlada. El administrador puede editar productos y precios del menú base. Las promociones se gestionan aparte, como descuentos por porcentaje con vigencia temporal, y no alteran el precio base.

## c. Gestión de ventas y pedidos

### i. ¿Cómo se toman actualmente los pedidos (en papel, verbalmente, por app)?

En su mayoría en papel, lo que retrasa el flujo y genera confusiones entre las áreas.

### ii. ¿Desea que los pedidos se hagan desde una terminal, dispositivo móvil o ambos?

Desde un dispositivo móvil (tablet). Cocina y bar visualizan los pedidos en una tablet o pantalla fija en su área.

### iii. ¿Quién debe tener permiso para ingresar y gestionar pedidos?

El cliente ingresa los pedidos. Los administradores de cocina y de bar ven y gestionan los pedidos de su área, y cambian su estado (pendiente, en preparación, listo). El cliente ve ese el la línea de tiempo (seguimiento) de su pedido.

### iv. ¿Desea incluir distintas formas de pago (efectivo, tarjeta, transferencia)?

Sí:

- Tarjeta: mediante una pasarela de pago integrada. El sistema no almacena datos de la tarjeta y la confirmación es automática.

- Transferencia: el cliente sube el comprobante y el administrador lo verifica. (bot)

- Efectivo: lo confirma el administrador al recibir el dinero.

### v. ¿Debe el sistema generar comprobantes o facturas?

Sí. El sistema genera una factura por cada pago confirmado, con numeración única y el detalle del consumo (orden de compra).

## d. Gestión de usuarios y roles

### i. ¿Qué tipos de usuarios tendrá el sistema?

Clientes interesados en el bar y personal del negocio (operativo, administrativo y técnico).

### ii. ¿Qué permisos o accesos específicos tendrá cada tipo de usuario?

- **Cliente:** menú, reserva de mesa, seguimiento y CRUD(agregar, editar, ver) del pedido, pago y encuesta de satisfacción.

- **Mesero:** registro de pedidos por mesa.

- **Administrador de cocina:** inventario y pedidos de cocina.

- **Administrador de bar:** inventario y pedidos del bar.

- **Asistente:** gestión de reservas.

- **Administrador:** menú, promociones, verificación de transferencias, generación de comprobantes (sistema de cobro), reservas, pedidos y reportes.

- **Superadministrador:** usuarios, roles, configuración, bitácora y mantenimiento. Accede a todo el sistema.

### iii. ¿Desea que los usuarios se autentiquen con contraseña, PIN u otro método?

- **Personal:** usuario y contraseña, según su rol.

- **Clientes:** no necesitan registrarse. Acceden al aplicativo vinculado a su mesa (reserva), que se activa al reservar o ingresar al local y caduca al cerrar la cuenta.

- **Equipo del local:** el menú y el seguimiento también son accesibles desde el equipo disponible en el establecimiento.

## e. Gestión de tarjeta y atención al cliente

### i. ¿Cómo está organizado el bar en términos de tarjetas?

Los pagos con tarjeta se realizan desde la plataforma mediante una pasarela de pago. El cliente ingresa los datos de su tarjeta en la pasarela, que procesa el cobro. El sistema solo guarda la referencia de la transacción, no los datos de la tarjeta.

### ii. ¿Se requiere llevar seguimiento del estado de cada tarjeta (número de comidas, vacía, reducción de comidas)?

El cliente solicita la cuenta, y el sistema la cierra y calcula el total con los descuentos aplicados. Luego el cliente elige su forma de pago, y el pago se confirma así:

- **Tarjeta:** automáticamente.

- **Transferencia:** tras la verificación del administrador.

- **Efectivo:** tras la confirmación del mesero o cajero.

El administrador interviene realizando toda la gestion.

### iii. ¿Cómo se mide la satisfacción del cliente?

Después de confirmarse el pago, el sistema presenta una encuesta automática con dos calificaciones, de 1 a 5 estrellas:

- **Calificación del mesero:** evalúa la atención recibida.

- **Calificación del servicio general:** evalúa la experiencia en el local.

## f. Reportes y estadísticas

### i. ¿Qué tipo de reportes desea obtener del sistema? (ventas diarias, productos más vendidos, desempeño por empleado)

- Ventas diarias, calculadas por jornada. Como el horario cruza la medianoche, una jornada abarca de la tarde hasta la madrugada.

- Productos más vendidos.

- Índice de pedidos por mesero.

- Nivel de satisfacción de los clientes, en gráfico de pastel.

- Comparación de ventas por día de la semana, en gráfico de barras.

- Horas de mayor afluencia y ticket promedio.

- Índice de clientes que se quedan al espectáculo.

### ii. ¿Con qué frecuencia necesita estos reportes?

Se actualizan cada jornada. Tienen acceso el administrador y el superadministrador.

### iii. ¿Deben los reportes poder exportarse (PDF, Excel)?

La exportación es opcional, porque la plataforma ya muestra el resumen con todos los gráficos. Quien lo requiera podrá exportar un Excel con una hoja por cada tema de reporte.

## g. Seguridad y acceso

### i. ¿Qué nivel de seguridad espera que tenga el sistema?

Alto, porque el sistema gestiona usuarios, pagos y administración. Incluye comunicación cifrada (HTTPS), control de acceso por rol validado en el servidor y verificación en dos pasos para los roles administrativos.

### ii. ¿Desea llevar un registro de acciones realizadas por los usuarios (bitácora)?

Sí. Se registran las acciones del personal (pedidos, pagos, inventario, promociones, reservas y usuarios), y el registro no puede editarse ni borrarse. Las acciones de los clientes solo se registran si estos deciden registrarse.

### iii. ¿Hay alguna información que debe estar encriptada o protegida de forma especial?

Sí:

- Las contraseñas, que se guardan con hash.

- Los datos de pago, que se delegan a la pasarela y no se almacenan.

- Los datos personales de clientes y reservas.

## h. Infraestructura y despliegue

### i. ¿El sistema debe estar disponible en la nube o solo en la red local del bar?

En la nube, porque los clientes necesitan acceder desde internet. Se contemplan respaldos automáticos de la base de datos.

### ii. ¿Qué dispositivos se usarán para acceder al sistema? (PC, tablets, celulares)

- Tablets o pantallas fijas: cocina y bar, meseros y mesas (cliente).

- PC o tablet: asistente y administración.

El sistema debe ser responsivo para todos ellos.

### iii. ¿Se requiere acceso remoto para el administrador?

Sí, para el superadministrador, que pertenece al equipo técnico y no al personal del bar. El administrador (gerente) también puede consultar el sistema de forma remota.

## i. Interfaz y experiencia de usuario

### i. ¿Tiene alguna preferencia sobre el diseño del sistema (colores, logos, experiencia visual)?

- **Clientes:** diseño interactivo, muy visual y atractivo.

- **Área administrativa:** diseño limpio y eficiente, sin saturación.

### ii. ¿Desea que el sistema sea responsivo y accesible desde móviles?

Sí. Debe funcionar bien en tablets y PC.

### iii. ¿Qué tan intuitiva desea que sea la interfaz para los usuarios no técnicos?

Muy intuitiva, porque lo usarán desde clientes hasta personal administrativo con distintos niveles de conocimiento técnico.

## j. Escenarios especiales

### i. ¿Desea que el sistema gestione promociones u ofertas especiales?

Sí. El administrador gestiona descuentos por porcentaje, con fecha de inicio y fin, aplicables a productos o combos. Al vencer, el precio vuelve automáticamente al valor base.

### ii. ¿Cómo se manejan los productos agotados?

El sistema los marca como agotados cuando el stock llega a cero. Todos los usuarios los van a ver sombreados y en con una señalización de agotado (que este no se pueda seleccionar en el pedido). El cliente no puede agregarlos a un pedido.

### iii. ¿Hay horarios de funcionamiento específicos que deben considerarse?

- **Clientes:** mayor uso entre las 7 pm y las 2 am.

- **Administración:** mayor uso desde las 5 pm, para inventario, cuadre de cuentas y demás tareas.

- **Reportes:** se calculan por jornada al finalizar.
