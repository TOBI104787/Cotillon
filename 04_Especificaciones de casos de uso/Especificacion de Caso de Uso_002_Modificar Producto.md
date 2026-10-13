# Especificación de Caso de Uso: Modificar Producto

## Nombre del caso de uso
Modificar producto

## Actor
Usuario del sistema

## Objetivo
Permitir al usuario modificar la información de un producto que ya se encuentra registrado en el sistema, para mantener actualizados sus datos.

## Precondiciones
- El usuario debe tener acceso al sistema.
- El producto que se desea modificar debe estar registrado.

## Postcondiciones
- El producto queda actualizado con la nueva información ingresada.
- Los cambios quedan guardados en el sistema.

## Flujo principal
1. El usuario selecciona la opción **"Modificar producto"**.
2. El sistema solicita seleccionar o buscar el producto que desea modificar.
3. El usuario selecciona el producto.
4. El sistema muestra la información actual del producto.
5. El usuario modifica los datos que necesita actualizar.
6. El sistema verifica que los datos ingresados sean válidos.
7. El usuario confirma los cambios.
8. El sistema guarda la información modificada.
9. El sistema informa al usuario que el producto fue modificado correctamente.

## Flujos alternativos

### FA1 - Producto no encontrado
1. El usuario busca un producto que no se encuentra registrado.
2. El sistema informa que no se encontró el producto.
3. El usuario realiza una nueva búsqueda o cancela la operación.

### FA2 - Dato inválido
1. El usuario ingresa un dato que no es válido.
2. El sistema informa el error correspondiente.
3. El usuario corrige el dato.
4. El sistema continúa con el flujo principal.

### FA3 - Categoría no seleccionada
1. El usuario modifica el producto y no selecciona una categoría.
2. El sistema informa que el producto debe pertenecer a una categoría.
3. El usuario selecciona una categoría.
4. El sistema continúa con el flujo principal.

### FA4 - Precio inválido
1. El usuario ingresa un precio igual o menor a cero.
2. El sistema informa que el precio ingresado no es válido.
3. El usuario corrige el precio.
4. El sistema continúa con el flujo principal.

### FA5 - Cancelar modificación
1. El usuario selecciona la opción **"Cancelar"**.
2. El sistema cancela la operación.
3. El producto mantiene la información que tenía antes de comenzar la modificación.

## Datos involucrados

| Dato | Descripción |
|---|---|
| ID del producto | Identificador único del producto |
| Nombre | Nombre del producto |
| Precio | Precio de venta del producto |
| Stock | Cantidad disponible del producto |
| ID de categoría | Identificador de la categoría a la que pertenece |

## Reglas de negocio relacionadas
- Cada producto debe pertenecer a una categoría.
- No se permite establecer un precio igual o menor a cero.
- El producto debe existir en el sistema para poder ser modificado.

## Resultado esperado
El producto seleccionado queda actualizado con los nuevos datos y la información modificada se guarda correctamente en el sistema.
