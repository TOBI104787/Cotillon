# Especificación de Caso de Uso: Registrar Gasto

## Nombre del caso de uso
Registrar gasto

## Actor
Usuario del sistema

## Objetivo
Permitir al usuario registrar un gasto del cotillón para mantener un control de los egresos del negocio.

## Precondiciones
- El usuario debe tener acceso al sistema.

## Postcondiciones
- El gasto queda registrado en el sistema.
- El gasto queda disponible para futuras consultas y para el resumen de ingresos y egresos.

## Flujo principal
1. El usuario selecciona la opción **"Registrar gasto"**.
2. El sistema muestra un formulario para ingresar los datos del gasto.
3. El usuario ingresa la descripción, la fecha y el monto del gasto.
4. El sistema verifica que los datos ingresados sean válidos.
5. El usuario confirma el registro.
6. El sistema guarda el gasto.
7. El sistema informa al usuario que el gasto fue registrado correctamente.

## Flujos alternativos

### FA1 - Falta un dato obligatorio
1. El usuario intenta registrar el gasto sin completar la descripción, la fecha o el monto.
2. El sistema informa qué dato falta.
3. El usuario completa la información solicitada.
4. El sistema continúa con el flujo principal.

### FA2 - Monto inválido
1. El usuario ingresa un monto igual o menor a cero.
2. El sistema informa que el monto debe ser mayor a cero.
3. El usuario corrige el monto.
4. El sistema continúa con el flujo principal.

### FA3 - Fecha inválida
1. El usuario ingresa una fecha incorrecta.
2. El sistema informa que debe ingresar una fecha válida.
3. El usuario corrige la fecha.
4. El sistema continúa con el flujo principal.

### FA4 - Cancelar registro
1. El usuario selecciona la opción **"Cancelar"**.
2. El sistema cancela la operación.
3. El gasto no queda registrado.

## Datos involucrados

| Dato | Descripción |
|---|---|
| ID del gasto | Identificador único del gasto |
| Descripción | Motivo o concepto del gasto, por ejemplo, alquiler |
| Fecha | Fecha en la que se realizó el gasto |
| Monto | Importe del gasto |

## Reglas de negocio relacionadas
- Todo gasto debe incluir una descripción, una fecha y un monto.
- El monto del gasto debe ser mayor a cero.
- Los gastos registrados se utilizan para consultar los egresos y generar el resumen de ingresos y egresos.

## Resultado esperado
El gasto queda registrado correctamente con su descripción, fecha y monto, y puede ser consultado posteriormente.
