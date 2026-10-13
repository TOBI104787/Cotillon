# Especificación de Caso de Uso: Consultar Ventas

## Nombre del caso de uso
Consultar ventas

## Actor
Usuario del sistema

## Objetivo
Permitir al usuario consultar las ventas registradas en el sistema y revisar las ventas realizadas en una fecha o durante un período determinado.

## Precondiciones
- El usuario debe tener acceso al sistema.
- Deben existir ventas registradas para que se muestren resultados.

## Postcondiciones
- El sistema muestra las ventas que coinciden con los criterios de búsqueda.
- La información de las ventas consultadas queda disponible para que el usuario la revise.

## Flujo principal
1. El usuario selecciona la opción **"Consultar ventas"**.
2. El sistema muestra las opciones para consultar las ventas por fecha o por período.
3. El usuario selecciona el criterio de consulta.
4. El usuario ingresa la fecha o el período que desea consultar.
5. El sistema verifica que los datos ingresados sean válidos.
6. El sistema busca las ventas registradas que coinciden con los criterios seleccionados.
7. El sistema muestra el listado de ventas encontradas, incluyendo la fecha y el monto total de cada venta.
8. El usuario revisa la información de las ventas.

## Flujos alternativos

### FA1 - No hay ventas para la fecha o el período indicado
1. El usuario realiza una consulta con una fecha o un período válido.
2. El sistema no encuentra ventas que coincidan con los criterios ingresados.
3. El sistema informa que no se encontraron ventas para esa consulta.

### FA2 - Fecha o período inválido
1. El usuario ingresa una fecha incorrecta o un período no válido.
2. El sistema informa que debe ingresar una fecha o un período válido.
3. El usuario corrige los datos.
4. El sistema continúa con el flujo principal.

### FA3 - No se ingresan criterios de consulta
1. El usuario intenta realizar la consulta sin indicar una fecha o un período.
2. El sistema solicita que complete los criterios de consulta.
3. El usuario ingresa los datos solicitados.
4. El sistema continúa con el flujo principal.

### FA4 - Cancelar consulta
1. El usuario selecciona la opción **"Cancelar"**.
2. El sistema cancela la operación.
3. El usuario regresa a la pantalla anterior.

## Datos involucrados

| Dato | Descripción |
|---|---|
| Fecha | Fecha en la que se realizó la venta |
| Período | Intervalo de fechas que desea consultar el usuario |
| ID de venta | Identificador único de la venta |
| Total | Monto total de la venta |

## Reglas de negocio relacionadas
- Toda venta registrada debe tener una fecha y un monto total.
- Las consultas deben realizarse con una fecha o un período válido.
- El sistema debe mostrar las ventas que coincidan con la fecha o el período indicado.

## Resultado esperado
El sistema muestra el listado de ventas correspondiente a la fecha o al período seleccionado, o informa que no existen ventas para esa consulta.
