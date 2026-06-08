**Reglas de negocio:**

**Hechos:** 
Cada producto pertenece a una categoría. 
Toda venta tiene una fecha de venta registrada. 
Toda compra tiene una fecha de compra registrada 
Cada pago de una venta tiene un metodo de pago registrado. 
Cada producto cuenta con una cantidad disponible en stock.

**Restricciones:** 
No vender productos sin stock. 
Dar de baja lógica un producto cuando deja de existir a nivel comercial. 
No registrar productos sin nombre o sin precio. 
No registrar ventas con cantidades menores o iguales a cero.

**Acciones disparadoras:** 
Si se alcanza el stock mínimo de un producto se da una alerta. 
Cuando finaliza el día, generar un reporte de ventas diarias. 
Cuando se registra una venta, se actualiza automáticamente el stock.

**Cálculos:** 
El total de la venta se calcula sumando los precios de los productos vendidos.
El resumen financiero se calcula con ingresos menos egresos. 
El total de ingresos diarios se calcula sumando todas las ventas realizadas en el día.

**Inferencias:** 
Si los gastos superan los ingresos, el negocio presenta pérdidas. 

