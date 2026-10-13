# Especificación de Caso de Uso 9: Consultar Gastos

## 1. Nombre del caso de uso
Consultar Gastos

## 2. Actor principal
Usuario del sistema

## 3. Objetivo
Permitir al usuario consultar los gastos que fueron registrados en el sistema para revisar la información de los egresos del negocio.

## 4. Precondiciones
- El usuario debe tener acceso al sistema.
- Debe haber gastos registrados para que se muestren resultados.

## 5. Postcondiciones
- El sistema muestra los gastos que coinciden con los criterios de consulta.
- La información registrada no se modifica.

## 6. Flujo principal
1. El usuario ingresa al sistema.
2. Selecciona la opción **Consultar gastos**.
3. El sistema muestra los criterios disponibles para realizar la consulta.
4. El usuario ingresa o selecciona los criterios necesarios, como una fecha o un período.
5. El sistema valida los criterios ingresados.
6. El sistema busca los gastos que coinciden con esos criterios.
7. El sistema muestra los gastos encontrados, incluyendo descripción, fecha y monto.
8. El usuario revisa la información y finaliza la consulta.

## 7. Flujos alternativos
- **A1. No se encuentran gastos:** el sistema informa que no hay gastos registrados que coincidan con los criterios seleccionados.
- **A2. Criterios inválidos:** el sistema informa el error y solicita que se corrijan los datos de la consulta.
- **A3. Criterios incompletos:** el sistema solicita que se ingresen los datos necesarios para realizar la consulta.
- **A4. Cancelar consulta:** el usuario cancela la operación y el sistema vuelve al menú anterior.

## 8. Datos involucrados
- Identificador del gasto.
- Descripción del gasto.
- Fecha.
- Monto.

## 9. Reglas de negocio relacionadas
- Cada gasto registrado debe tener una descripción, una fecha y un monto.
- El monto del gasto debe ser mayor que cero.
- Los gastos consultados deben corresponder a los criterios ingresados por el usuario.
- Los gastos registrados se utilizan para consultar los egresos y elaborar el resumen de ingresos y egresos.

## 10. Frecuencia de uso
Se utiliza cuando el usuario necesita revisar los gastos registrados en el negocio.
