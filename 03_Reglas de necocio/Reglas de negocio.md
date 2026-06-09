# **Reglas de negocio:**

## **Hechos:** 
1. Cada producto pertenece a una categoría.
2. Toda venta tiene una fecha de venta registrada.
3. Toda compra tiene una fecha de compra registrada.
4. Cada pago de una venta se paga con un metodo de pago.
5. Se lleva un registro de la cantidad en stock de cada producto.

## **Restricciones:** 
1. No se venden productos sin stock. 
2. Dar de baja un producto cuando deja de existir a nivel comercial.
3. No registrar productos sin nombre o sin precio.
4. No registrar ventas con cantidades de stock menores o iguales a cero.

## **Acciones disparadoras:** 
1. Si se alcanza el stock mínimo de seguridad se dara una alerta la proxima vez que se abra el sistema.

## **Cálculos:** 
1. El precio total de la venta se calcula sumando los precios de los productos vendidos multiplicado por las unidades de dichos productos.
2. El resumen financiero se calcula con ingresos menos egresos.
3. El total de ingresos diarios se calcula sumando todas las ventas realizadas en el día.

## **Inferencias:** 
1. Si los gastos superan los ingresos, el negocio es deficitario.
