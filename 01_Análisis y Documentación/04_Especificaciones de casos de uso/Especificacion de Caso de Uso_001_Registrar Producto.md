# Especificación de Caso de Uso: Registrar Producto

## Nombre del caso de uso
Registrar producto

## Actor
Empleado o responsable del negocio

## Objetivo
Permitir al usuario registrar un nuevo producto del cotillón, ingresando la información necesaria para mantener actualizado el catálogo de productos.

## Precondiciones
- El usuario debe tener la sesion iniciada.
- Debe existir al menos una categoría disponible para asociar el producto.


## Flujo principal
1. El usuario ingresa:
   - Nombre del producto.
   - Precio.
   - Stock disponible.
   - Categoría a la que pertenece.
2. El sistema verifica que los datos ingresados sean válidos y pide confirmación al usuario.
3. El usuario confirma el registro.
4. El sistema guarda la información del nuevo producto.
5. El sistema informa al usuario que el producto fue registrado correctamente.

## Flujos alternativos

### FA1 - Faltan datos
1. El usuario intenta registrar el producto sin completar uno o más datos obligatorios.
2. El sistema informa qué datos faltan.
3. El usuario completa la información solicitada.
4. El sistema continúa con el flujo principal.

### FA2 - Precio inválido
1. El usuario ingresa un precio igual o menor a cero.
2. El sistema informa que el precio ingresado no es válido.
3. El usuario ingresa un precio valido.
4. El sistema continúa con el flujo principal.

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
- No se permite registrar un producto con un precio igual o menor a cero.
- El producto debe contar con la información necesaria para poder ser registrado.
- 
## Postcondiciones
- El producto queda registrado en el sistema.
- El producto queda asociado a una categoría.
- El producto queda disponible para ser consultado y utilizado en futuras ventas.

## Resultado esperado
El producto se registra correctamente y queda disponible en el sistema con su información correspondiente.
