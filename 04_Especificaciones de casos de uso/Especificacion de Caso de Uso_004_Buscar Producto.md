# Especificación de Caso de Uso: Buscar Producto

## Nombre del caso de uso
Buscar producto

## Actor
Usuario del sistema

## Objetivo
Permitir al usuario encontrar rápidamente un producto registrado en el sistema mediante su nombre.

## Precondiciones
- El usuario debe tener acceso al sistema.
- Debe existir al menos un producto registrado para realizar una búsqueda.

## Postcondiciones
- El sistema muestra los productos que coinciden con el nombre ingresado.
- El usuario puede consultar la información del producto encontrado.

## Flujo principal
1. El usuario selecciona la opción **"Buscar producto"**.
2. El sistema muestra un campo para ingresar el nombre del producto.
3. El usuario ingresa el nombre o parte del nombre del producto que desea buscar.
4. El usuario confirma la búsqueda.
5. El sistema busca los productos que coinciden con el texto ingresado.
6. El sistema muestra los resultados encontrados.
7. El usuario selecciona un producto para consultar su información.

## Flujos alternativos

### FA1 - Producto no encontrado
1. El usuario realiza una búsqueda.
2. El sistema no encuentra productos que coincidan con el texto ingresado.
3. El sistema informa que no se encontraron productos.
4. El usuario puede realizar una nueva búsqueda.

### FA2 - Búsqueda sin ingresar un nombre
1. El usuario intenta realizar una búsqueda sin ingresar un nombre.
2. El sistema solicita que ingrese el nombre o parte del nombre del producto.
3. El usuario ingresa el texto correspondiente.
4. El sistema continúa con el flujo principal.

### FA3 - Cancelar búsqueda
1. El usuario selecciona la opción **"Cancelar"**.
2. El sistema cancela la operación.
3. El usuario regresa a la pantalla anterior.

## Datos involucrados

| Dato | Descripción |
|---|---|
| Nombre del producto | Nombre utilizado para realizar la búsqueda |
| ID del producto | Identificador único del producto |
| Precio | Precio de venta del producto |
| Stock | Cantidad disponible del producto |
| ID de categoría | Identificador de la categoría a la que pertenece |

## Reglas de negocio relacionadas
- Los productos deben estar registrados en el sistema para poder ser encontrados.
- La búsqueda se realiza por nombre del producto.

## Resultado esperado
El sistema muestra los productos que coinciden con la búsqueda realizada y permite consultar la información del producto seleccionado.
