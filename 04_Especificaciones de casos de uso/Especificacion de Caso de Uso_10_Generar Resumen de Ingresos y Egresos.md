# Especificación de Caso de Uso 10: Generar Resumen de Ingresos y Egresos

## 1. Nombre del caso de uso
Generar Resumen de Ingresos y Egresos

## 2. Actor principal
Usuario del sistema

## 3. Objetivo
Permitir al usuario obtener un resumen de los ingresos provenientes de las ventas y de los egresos correspondientes a los gastos registrados durante un período determinado.

## 4. Precondiciones
- El usuario debe tener acceso al sistema.
- El usuario debe indicar un período válido para la consulta.

## 5. Postcondiciones
- El sistema muestra el resumen de ingresos, egresos y balance del período seleccionado.
- Los datos de ventas y gastos existentes no se modifican.

## 6. Flujo principal
1. El usuario ingresa al sistema.
2. Selecciona la opción **Generar resumen de ingresos y egresos**.
3. El sistema solicita el período que desea consultar.
4. El usuario ingresa o selecciona las fechas de inicio y fin.
5. El sistema valida que el período ingresado sea válido.
6. El sistema consulta las ventas realizadas dentro del período seleccionado.
7. El sistema consulta los gastos registrados dentro del mismo período.
8. El sistema calcula el total de ingresos a partir de las ventas.
9. El sistema calcula el total de egresos a partir de los gastos.
10. El sistema calcula el balance restando los egresos a los ingresos.
11. El sistema muestra el período consultado, el total de ingresos, el total de egresos y el balance.
12. El usuario revisa el resumen y finaliza la operación.

## 7. Flujos alternativos
- **A1. Período inválido:** si la fecha de inicio es posterior a la fecha de fin o las fechas ingresadas no son válidas, el sistema informa el error y solicita corregir el período.
- **A2. No hay registros en el período:** el sistema informa que no se encontraron ventas ni gastos para el período seleccionado y muestra los totales en cero, según corresponda.
- **A3. Criterios incompletos:** el sistema solicita que se complete el período necesario para generar el resumen.
- **A4. Cancelar operación:** el usuario cancela la consulta y el sistema vuelve al menú anterior.

## 8. Datos involucrados
- Período consultado.
- Fecha de inicio.
- Fecha de fin.
- Total de ingresos.
- Total de egresos.
- Balance.

## 9. Reglas de negocio relacionadas
- Los ingresos del resumen se obtienen a partir de las ventas registradas en el período seleccionado.
- Los egresos del resumen se obtienen a partir de los gastos registrados en el período seleccionado.
- El balance se calcula como **ingresos - egresos**.
- El período seleccionado debe ser válido.
- La generación del resumen no debe modificar las ventas ni los gastos registrados.

## 10. Frecuencia de uso
Se utiliza cuando el usuario necesita revisar los ingresos, los egresos y el balance del negocio durante un período determinado.
