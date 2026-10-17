# Especificación de Caso de Uso: Registrar Producto

## Nombre del caso de uso
Registrar producto

## Actor
Usuario del sistema

## Objetivo
Permitir al usuario registrar un nuevo producto del cotillón, ingresando la información necesaria para mantener actualizado el catálogo de productos.

## Precondiciones
- El usuario debe tener acceso al sistema.
- Debe existir al menos una categoría disponible para asociar el producto.

## Postcondiciones
- El producto queda registrado en el sistema.
- El producto queda asociado a una categoría.
- El producto queda disponible para ser consultado y utilizado en futuras ventas.

## Flujo principal
1. El usuario selecciona la opción **"Registrar producto"**.
2. El sistema muestra un formulario para ingresar los datos del producto.
3. El usuario ingresa:
   - Nombre del producto.
   - Precio.
   - Stock disponible.
   - Categoría a la que pertenece.
4. El sistema verifica que los datos ingresados sean válidos.
5. El usuario confirma el registro.
6. El sistema guarda la información del nuevo producto.
7. El sistema informa al usuario que el producto fue registrado correctamente.

## Flujos alternativos

### FA1 - Falta un dato obligatorio
1. El usuario intenta registrar el producto sin completar uno o más datos obligatorios.
2. El sistema informa qué datos faltan.
3. El usuario completa la información solicitada.
4. El sistema continúa con el flujo principal.

### FA2 - Precio inválido
1. El usuario ingresa un precio igual o menor a cero.
2. El sistema informa que el precio ingresado no es válido.
3. El usuario corrige el precio.
4. El sistema continúa con el flujo principal.

### FA3 - Categoría no seleccionada
1. El usuario intenta registrar el producto sin seleccionar una categoría.
2. El sistema informa que debe seleccionar una categoría.
3. El usuario selecciona una categoría.
4. El sistema continúa con el flujo principal.

### FA4 - Cancelar registro
1. El usuario selecciona la opción **"Cancelar"**.
2. El sistema cancela la operación.
3. El producto no es registrado.

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

## Resultado esperado
El producto se registra correctamente y queda disponible en el sistema con su información correspondiente.
