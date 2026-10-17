# Especificación de Caso de Uso 11: Generar Reporte de Ventas

## 1. Nombre del caso de uso
Generar Reporte de Ventas

## 2. Actor principal
Usuario del sistema

## 3. Objetivo
Permitir al usuario generar un reporte con información de las ventas registradas para revisar la actividad del negocio durante un período determinado.

## 4. Precondiciones
- El usuario debe tener acceso al sistema.
- Debe ingresar o seleccionar un período válido para el reporte.

## 5. Postcondiciones
- El sistema muestra el reporte de ventas correspondiente al período seleccionado.
- Los registros de ventas no se modifican.

## 6. Flujo principal
1. El usuario ingresa al sistema.
2. Selecciona la opción **Generar reporte de ventas**.
3. El sistema solicita el período que desea consultar.
4. El usuario ingresa o selecciona la fecha de inicio y la fecha de fin.
5. El sistema valida que el período sea correcto.
6. El sistema busca las ventas registradas dentro del período seleccionado.
7. El sistema organiza la información encontrada para presentarla en el reporte.
8. El sistema muestra el reporte con los datos disponibles de las ventas, como la fecha y el total de cada venta.
9. El usuario revisa el reporte y finaliza la operación.

## 7. Flujos alternativos
- **A1. Período inválido:** el sistema informa que las fechas ingresadas no son válidas y solicita corregirlas.
- **A2. No hay ventas en el período:** el sistema informa que no se encontraron ventas para las fechas seleccionadas.
- **A3. Datos incompletos:** el sistema solicita completar las fechas necesarias para generar el reporte.
- **A4. Cancelar operación:** el usuario cancela la generación del reporte y vuelve al menú anterior.

## 8. Datos involucrados
- Fecha de inicio.
- Fecha de fin.
- Identificador de la venta.
- Fecha de cada venta.
- Total de cada venta.

## 9. Reglas de negocio relacionadas
- El período seleccionado debe ser válido.
- El reporte debe incluir únicamente las ventas que correspondan al período consultado.
- Cada venta registrada debe tener una fecha y un total.
- La generación del reporte no debe modificar los datos de las ventas.

## 10. Frecuencia de uso
Se utiliza cuando el usuario necesita revisar o consultar las ventas realizadas durante un período determinado.
