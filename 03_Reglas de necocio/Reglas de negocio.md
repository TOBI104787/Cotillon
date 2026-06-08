**Reglas de negocio:**

**Hechos:** 
Cada producto pertenece a una categoría. 
Toda venta tiene una fecha de venta registrada. 
Toda compra tiene una fecha de compra registrada 
Cada pago de una venta se paga con un metodo de pago. 
Se lleva un registro de la cantidad en stock de cada producto.

**Restricciones:** 
No se venden productos sin stock. 
Dar de baja un producto cuando deja de existir a nivel comercial. 
No registrar productos sin nombre o sin precio. 
No registrar ventas con cantidades de stock menores o iguales a cero.

**Acciones disparadoras:** 
Si se alcanza el stock mínimo de seguridad se dara una alerta la proxima vez que se abra el sistema.  

**Cálculos:** 
El precio total de la venta se calcula sumando los precios de los productos vendidos multiplicado por las unidades de dichos productos.
El resumen financiero se calcula con ingresos menos egresos. 
El total de ingresos diarios se calcula sumando todas las ventas realizadas en el día.

**Inferencias:** 
Si los gastos superan los ingresos, el negocio presenta pérdidas. 

