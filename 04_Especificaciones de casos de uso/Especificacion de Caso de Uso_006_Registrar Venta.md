# Especificación de Caso de Uso: Registrar Venta

## Nombre del caso de uso
Registrar venta

## Actor
Usuario del sistema

## Objetivo
Permitir al usuario registrar una venta realizada en el cotillón, indicando los productos vendidos y las cantidades correspondientes, para mantener actualizado el registro de ventas.

## Precondiciones
- El usuario debe tener acceso al sistema.
- Debe existir al menos un producto registrado.
- Los productos que se incluirán en la venta deben tener stock suficiente.

## Postcondiciones
- La venta queda registrada en el sistema con su fecha y monto total.
- Los productos vendidos y sus cantidades quedan asociados a la venta.
- El stock de cada producto vendido se actualiza descontando las cantidades vendidas.

## Flujo principal
1. El usuario selecciona la opción **"Registrar venta"**.
2. El sistema muestra la opción para agregar productos a la venta.
3. El usuario busca y selecciona un producto.
4. El usuario indica la cantidad que desea vender.
5. El sistema verifica que haya stock suficiente para esa cantidad.
6. El sistema agrega el producto y su cantidad al detalle de la venta.
7. El usuario repite los pasos 3 a 6 para agregar otros productos, si corresponde.
8. El sistema calcula el subtotal de cada producto y el monto total de la venta.
9. El usuario revisa la información y confirma la venta.
10. El sistema registra la venta con la fecha y el monto total.
11. El sistema actualiza el stock de los productos vendidos.
12. El sistema informa que la venta fue registrada correctamente.

## Flujos alternativos

### FA1 - Producto no encontrado
1. El usuario busca un producto que no está registrado.
2. El sistema informa que no se encontró el producto.
3. El usuario realiza una nueva búsqueda o continúa con otro producto.

### FA2 - Stock insuficiente
1. El usuario ingresa una cantidad mayor al stock disponible.
2. El sistema informa que no hay stock suficiente.
3. El usuario modifica la cantidad o quita el producto de la venta.
4. El sistema continúa cuando la cantidad ingresada es válida.

### FA3 - Cantidad inválida
1. El usuario ingresa una cantidad igual o menor a cero.
2. El sistema informa que la cantidad debe ser mayor a cero.
3. El usuario corrige la cantidad.
4. El sistema continúa con el flujo principal.

### FA4 - La venta no contiene productos
1. El usuario intenta confirmar una venta sin productos.
2. El sistema informa que debe agregar al menos un producto.
3. El usuario agrega uno o más productos, o cancela la operación.

### FA5 - Cancelar venta
1. El usuario selecciona la opción **"Cancelar"**.
2. El sistema cancela la operación.
3. La venta no queda registrada y el stock no se modifica.

## Datos involucrados

| Dato | Descripción |
|---|---|
| ID de venta | Identificador único de la venta |
| Fecha | Fecha en la que se realiza la venta |
| ID de producto | Identificador del producto vendido |
| Cantidad | Número de unidades vendidas de cada producto |
| Precio | Precio de venta del producto |
| Subtotal | Resultado de multiplicar el precio por la cantidad vendida |
| Total | Suma de los subtotales de los productos incluidos en la venta |

## Reglas de negocio relacionadas
- Toda venta debe registrar una fecha y un monto total.
- Toda venta debe incluir al menos un producto.
- No se puede registrar una venta si no hay stock suficiente para los productos y las cantidades indicadas.
- El total de la venta se calcula sumando los subtotales de los productos vendidos.
- Al registrar una venta, se debe actualizar el stock de los productos vendidos.

## Resultado esperado
La venta queda registrada correctamente con los productos, cantidades, fecha y monto total correspondientes, y el stock se actualiza según las cantidades vendidas.
