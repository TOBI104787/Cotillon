# Especificación de Caso de Uso: Registrar Categoría

## Nombre del caso de uso
Registrar categoría

## Actor
Usuario del sistema

## Objetivo
Permitir al usuario registrar una nueva categoría para organizar los productos del cotillón y facilitar su búsqueda.

## Precondiciones
- El usuario debe tener acceso al sistema.

## Postcondiciones
- La nueva categoría queda registrada en el sistema.
- La categoría queda disponible para asociarla a productos.

## Flujo principal
1. El usuario selecciona la opción **"Registrar categoría"**.
2. El sistema muestra un formulario para ingresar el nombre de la categoría.
3. El usuario ingresa el nombre de la nueva categoría.
4. El sistema verifica que el nombre haya sido ingresado.
5. El usuario confirma el registro.
6. El sistema guarda la nueva categoría.
7. El sistema informa al usuario que la categoría fue registrada correctamente.

## Flujos alternativos

### FA1 - Nombre de categoría vacío
1. El usuario intenta registrar una categoría sin ingresar un nombre.
2. El sistema informa que debe completar el nombre de la categoría.
3. El usuario ingresa el nombre.
4. El sistema continúa con el flujo principal.

### FA2 - Categoría ya existente
1. El usuario ingresa el nombre de una categoría que ya está registrada.
2. El sistema informa que esa categoría ya existe.
3. El usuario puede ingresar otro nombre o cancelar la operación.

### FA3 - Cancelar registro
1. El usuario selecciona la opción **"Cancelar"**.
2. El sistema cancela la operación.
3. La categoría no se registra.

## Datos involucrados

| Dato | Descripción |
|---|---|
| ID de categoría | Identificador único de la categoría |
| Nombre | Nombre de la categoría |

## Reglas de negocio relacionadas
- Cada producto debe pertenecer a una categoría.
- La categoría debe tener un nombre para poder registrarse.

## Resultado esperado
La categoría queda registrada y disponible para organizar los productos del cotillón.
