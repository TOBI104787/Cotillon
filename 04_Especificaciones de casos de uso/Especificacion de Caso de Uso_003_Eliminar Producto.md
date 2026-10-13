# Especificación de Caso de Uso: Eliminar Producto

## Nombre del caso de uso
Eliminar producto

## Actor
Usuario del sistema

## Objetivo
Permitir al usuario eliminar un producto que se encuentra registrado en el sistema cuando ya no sea necesario mantenerlo disponible.

## Precondiciones
- El usuario debe tener acceso al sistema.
- El producto que se desea eliminar debe estar registrado.

## Postcondiciones
- El producto queda eliminado del sistema.
- El producto deja de estar disponible para futuras consultas o registros de ventas.

## Flujo principal
1. El usuario selecciona la opción **"Eliminar producto"**.
2. El sistema solicita seleccionar o buscar el producto que desea eliminar.
3. El usuario selecciona el producto.
4. El sistema muestra la información del producto seleccionado.
5. El sistema solicita confirmar la eliminación.
6. El usuario confirma la eliminación.
7. El sistema verifica que el producto pueda ser eliminado.
8. El sistema elimina el producto.
9. El sistema informa al usuario que el producto fue eliminado correctamente.

## Flujos alternativos

### FA1 - Producto no encontrado
1. El usuario busca un producto que no se encuentra registrado.
2. El sistema informa que no se encontró el producto.
3. El usuario realiza una nueva búsqueda o cancela la operación.

### FA2 - Producto asociado a una venta
1. El usuario intenta eliminar un producto que ya fue incluido en una o más ventas.
2. El sistema informa que el producto no puede ser eliminado porque está asociado a una venta.
3. El sistema cancela la eliminación.
4. El producto permanece registrado.

### FA3 - Cancelar eliminación
1. El usuario selecciona la opción **"Cancelar"**.
2. El sistema cancela la operación.
3. El producto permanece registrado sin modificaciones.

## Datos involucrados

| Dato | Descripción |
|---|---|
| ID del producto | Identificador único del producto |
| Nombre | Nombre del producto |
| Precio | Precio de venta del producto |
| Stock | Cantidad disponible del producto |
| ID de categoría | Identificador de la categoría a la que pertenece |

## Reglas de negocio relacionadas
- No se podrán eliminar productos que hayan sido vendidos.
- El producto debe existir en el sistema para poder ser eliminado.

## Resultado esperado
El producto seleccionado se elimina correctamente del sistema, siempre que no esté asociado a una venta.
