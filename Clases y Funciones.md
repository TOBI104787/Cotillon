# Clases y funciones definidas — Sistema de Gestión para Cotillón

**Lenguaje:** Python  
**Paradigma:** Programación Orientada a Objetos (POO)  
**Base de datos prevista:** Mariadb  
**Proyecto:** Sistema de Gestión para un Cotillón

## 1. Objetivo

Este documento define una propuesta de clases, atributos y métodos para desarrollar el sistema en Python utilizando Programación Orientada a Objetos.

La propuesta contempla las funciones previstas para administrar productos y categorías, registrar y consultar ventas, registrar gastos y generar reportes.

Se separan:

- **Clases del modelo:** representan los datos y conceptos del negocio.
- **Clases de servicio:** contienen las operaciones y validaciones de los casos de uso.
- **Clases de acceso a datos:** se encargan de comunicarse con Mariadb.

Esta separación permite que las pantallas no tengan que contener directamente las consultas SQL ni las reglas del negocio.

---

## 2. Clases del modelo

### 2.1. `Provincia`

Representa una provincia donde se encuentra registrado un negocio.

**Atributos**
- `nombre: str`

**Métodos**
- `obtener_nombre() -> str`: devuelve el nombre de la provincia.
- `modificar_nombre(nombre: str) -> None`: actualiza el nombre.

### 2.2. `Localidad`

Representa una localidad y su provincia correspondiente.

**Atributos**
- `nombre: str`
- `provincia: Provincia`

**Métodos**
- `obtener_nombre() -> str`
- `obtener_provincia() -> Provincia`
- `cambiar_provincia(provincia: Provincia) -> None`

### 2.3. `Negocio`

Representa al cotillón que utiliza el sistema.

**Atributos**
- `cuit: str`
- `nombre: str`
- `direccion: str`
- `clave_de_acceso: str` — no debe guardarse como texto plano; almacenar un hash.
- `localidad: Localidad`

**Métodos**
- `modificar_datos(nombre: str, direccion: str, localidad: Localidad) -> None`
- `obtener_datos() -> dict`
- `validar_cuit(cuit: str) -> bool`

### 2.4. `Usuario`

Clase base para representar a una persona autorizada a utilizar el sistema.

**Atributos**
- `dni: str`
- `nombre: str`
- `apellido: str`
- `correo_electronico: str`
- `telefono: str`
- `nombre_de_usuario: str`
- `contrasena_hash: str`
- `negocio: Negocio`

**Métodos**
- `obtener_nombre_completo() -> str`
- `actualizar_datos(nombre: str, apellido: str, correo: str, telefono: str) -> None`
- `cambiar_contrasena(contrasena_actual: str, nueva_contrasena: str) -> bool`

**Nota:** `Usuario` es una clase general. Las contraseñas se deben almacenar mediante un hash seguro, nunca en texto plano.

### 2.5. `AdministradorSistema` (hereda de `Usuario`)

Representa a un administrador del sistema.

**Métodos**
- `puede_administrar_usuarios() -> bool`
- `puede_modificar_productos() -> bool`
- `puede_eliminar_productos() -> bool`

### 2.6. `TrabajadorNegocio` (hereda de `Usuario`)

Representa a un trabajador del cotillón.

**Métodos**
- `puede_registrar_ventas() -> bool`
- `puede_consultar_productos() -> bool`

**Nota sobre la base de datos actual:** el diagrama de MySQL Workbench muestra dos tablas separadas (`administradores_del_sistema` y `trabajadores_del_negocio`) con varios atributos en común. En Python se pueden representar mediante una clase base `Usuario` y dos subclases. Esto no obliga a unificar las tablas de Mariadb: la correspondencia entre clases y tablas debe resolverse en la capa de acceso a datos.

Los permisos indicados son una propuesta. Deben confirmarse con las reglas de negocio y con el profesor antes de programarlos.

### 2.7. `Categoria`

Representa una categoría de productos del cotillón.

**Atributos**
- `id_categoria: int`
- `nombre: str`
- `imagen: bytes | None`
- `negocio: Negocio`

**Métodos**
- `modificar_nombre(nombre: str) -> None`
- `modificar_imagen(imagen: bytes | None) -> None`
- `obtener_datos() -> dict`

### 2.8. `Producto`

Representa un producto disponible en el cotillón.

**Atributos**
- `id_producto: int`
- `nombre: str`
- `precio: Decimal`
- `stock: int`
- `imagen: bytes | None`
- `categoria: Categoria`

**Métodos**
- `modificar_datos(nombre: str, precio: Decimal, stock: int, categoria: Categoria) -> None`
- `actualizar_imagen(imagen: bytes | None) -> None`
- `hay_stock(cantidad: int) -> bool`
- `aumentar_stock(cantidad: int) -> None`
- `disminuir_stock(cantidad: int) -> None`
- `calcular_valor_stock() -> Decimal`

**Reglas que debe respetar**
- El precio debe ser mayor que cero.
- El stock no puede ser negativo.
- Todo producto debe pertenecer a una categoría.
- No se debe eliminar un producto asociado a una venta; puede desactivarse en lugar de borrarse físicamente.

### 2.9. `Venta`

Representa una venta realizada en el negocio.

**Atributos**
- `id_venta: int`
- `fecha: datetime`
- `vendedor: Usuario`
- `detalles: list[DetalleVenta]`
- `total: Decimal`

**Métodos**
- `agregar_detalle(detalle: DetalleVenta) -> None`
- `quitar_detalle(detalle: DetalleVenta) -> None`
- `calcular_total() -> Decimal`
- `validar_venta() -> bool`
- `obtener_resumen() -> dict`

**Reglas que debe respetar**
- La venta debe contener al menos un detalle.
- La cantidad de cada detalle debe ser mayor que cero.
- El total debe ser la suma de los subtotales.
- El stock debe verificarse antes de confirmar la venta.

### 2.10. `DetalleVenta`

Representa un producto incluido en una venta.

**Atributos**
- `id_detalle: int`
- `producto: Producto`
- `cantidad: int`
- `precio_unitario: Decimal`
- `subtotal: Decimal`

**Métodos**
- `calcular_subtotal() -> Decimal`
- `modificar_cantidad(cantidad: int) -> None`
- `obtener_datos() -> dict`

**Recomendación para la base de datos:** guardar `precio_unitario` al momento de la venta. De esa manera, si el precio actual del producto cambia, el detalle conserva el precio histórico con el que se realizó la operación.

### 2.11. `Gasto`

Representa un gasto del negocio.

**Atributos**
- `id_gasto: int`
- `descripcion: str`
- `fecha: date`
- `monto: Decimal`

**Métodos**
- `modificar_datos(descripcion: str, fecha: date, monto: Decimal) -> None`
- `validar_gasto() -> bool`
- `obtener_datos() -> dict`

**Reglas que debe respetar**
- La descripción no puede estar vacía.
- El monto debe ser mayor que cero.
- La fecha debe ser válida.

### 2.12. `ReporteResumen`

Representa el resumen de ingresos, egresos y balance para un período.

**Atributos**
- `fecha_desde: date`
- `fecha_hasta: date`
- `ingresos: Decimal`
- `egresos: Decimal`
- `balance: Decimal`

**Métodos**
- `calcular_ingresos(ventas: list[Venta]) -> Decimal`
- `calcular_egresos(gastos: list[Gasto]) -> Decimal`
- `calcular_balance() -> Decimal`
- `obtener_resultado() -> dict`

El reporte se puede calcular a partir de las ventas y los gastos consultados. No es obligatorio guardar cada resumen como una tabla: se puede generar cuando el usuario lo solicita.

---

## 3. Clases de servicio (operaciones de los casos de uso)

Las clases de servicio coordinan las operaciones, validan las reglas del negocio y solicitan a los repositorios que guarden o consulten información.

### 3.1. `ServicioAutenticacion`

**Funciones**
- `iniciar_sesion(nombre_usuario: str, contrasena: str) -> Usuario | None`: valida las credenciales y devuelve el usuario si son correctas.
- `cerrar_sesion() -> None`: finaliza la sesión activa.
- `verificar_permisos(usuario: Usuario, accion: str) -> bool`: comprueba si el usuario puede realizar una operación.

### 3.2. `ServicioProducto`

**Funciones**
- `registrar_producto(datos: dict) -> Producto`: valida los datos y registra un producto.
- `modificar_producto(id_producto: int, datos: dict) -> Producto`: busca el producto y modifica sus datos.
- `eliminar_producto(id_producto: int) -> bool`: verifica que el producto no esté asociado a ventas antes de eliminarlo o desactivarlo.
- `buscar_producto(nombre: str) -> list[Producto]`: busca coincidencias por nombre completo o parcial.
- `listar_productos() -> list[Producto]`: devuelve los productos registrados.
- `consultar_stock(id_producto: int) -> int`: devuelve el stock disponible.

### 3.3. `ServicioCategoria`

**Funciones**
- `registrar_categoria(datos: dict) -> Categoria`
- `modificar_categoria(id_categoria: int, datos: dict) -> Categoria`
- `eliminar_categoria(id_categoria: int) -> bool`: verifica que no tenga productos asociados antes de eliminarla.
- `buscar_categoria(nombre: str) -> list[Categoria]`
- `listar_categorias() -> list[Categoria]`

### 3.4. `ServicioVenta`

**Funciones**
- `crear_venta(usuario: Usuario) -> Venta`: prepara una nueva venta.
- `agregar_producto(venta: Venta, id_producto: int, cantidad: int) -> None`: comprueba que el producto exista y que haya stock suficiente.
- `quitar_producto(venta: Venta, id_producto: int) -> None`
- `calcular_total(venta: Venta) -> Decimal`
- `registrar_venta(venta: Venta) -> Venta`: valida la venta, guarda la operación y actualiza el stock dentro de una transacción.
- `consultar_ventas(fecha_desde: date, fecha_hasta: date) -> list[Venta]`

### 3.5. `ServicioGasto`

**Funciones**
- `registrar_gasto(datos: dict) -> Gasto`
- `consultar_gastos(fecha_desde: date, fecha_hasta: date) -> list[Gasto]`
- `obtener_gasto(id_gasto: int) -> Gasto | None`

### 3.6. `ServicioReporte`

**Funciones**
- `generar_resumen(fecha_desde: date, fecha_hasta: date) -> ReporteResumen`
- `generar_reporte_ventas(fecha_desde: date, fecha_hasta: date) -> list[Venta]`
- `exportar_reporte(datos: dict, formato: str) -> str`: exporta los datos si se define esa funcionalidad (por ejemplo, PDF o CSV).

---

## 4. Clases de acceso a datos

Estas clases centralizan la comunicación con Mariadb. Sus métodos realizan consultas y operaciones de persistencia. No deberían contener reglas de presentación.

### 4.1. `ConexionBD`

**Funciones**
- `conectar()`: abre la conexión con Mariadb.
- `obtener_conexion()`: devuelve la conexión activa.
- `cerrar()`: cierra la conexión.
- `iniciar_transaccion()`: inicia una transacción.
- `confirmar_transaccion()`: confirma los cambios.
- `revertir_transaccion()`: deshace los cambios ante un error.

### 4.2. Repositorios

Se recomienda crear un repositorio por grupo de datos:

| Clase | Funciones principales |
|---|---|
| `UsuarioRepositorio` | `buscar_por_usuario()`, `guardar()`, `actualizar()` |
| `NegocioRepositorio` | `buscar_por_cuit()`, `guardar()`, `actualizar()` |
| `ProductoRepositorio` | `guardar()`, `buscar_por_id()`, `buscar_por_nombre()`, `listar()`, `actualizar()`, `eliminar()` |
| `CategoriaRepositorio` | `guardar()`, `buscar_por_id()`, `buscar_por_nombre()`, `listar()`, `actualizar()`, `eliminar()` |
| `VentaRepositorio` | `guardar()`, `buscar_por_id()`, `buscar_por_periodo()`, `existe_venta_con_producto()` |
| `GastoRepositorio` | `guardar()`, `buscar_por_periodo()`, `buscar_por_id()` |
| `UbicacionRepositorio` | `buscar_localidad()`, `listar_provincias()`, `listar_localidades()` |

---

## 5. Relaciones entre las clases

Las relaciones principales propuestas son:

- Una `Provincia` puede tener muchas `Localidad`; cada localidad pertenece a una provincia.
- Una `Localidad` puede estar asociada a varios `Negocio`; cada negocio tiene una localidad.
- Un `Negocio` puede tener varios administradores, trabajadores y categorías.
- Una `Categoria` puede contener varios `Producto`; cada producto pertenece a una categoría.
- Un `Usuario` puede registrar muchas `Venta`.
- Una `Venta` contiene uno o varios `DetalleVenta`.
- Cada `DetalleVenta` corresponde a un `Producto`.
- El `ReporteResumen` utiliza las ventas y los gastos de un período para calcular sus importes.

---

## 6. Correspondencia con las tablas de MySQL Workbench

El modelo muestra estas tablas y campos principales:

| Tabla actual | Clase propuesta | Observación |
|---|---|---|
| `administradores_del_sistema` | `AdministradorSistema` | Comparte datos comunes con Usuario. |
| `trabajadores_del_negocio` | `TrabajadorNegocio` | Comparte datos comunes con Usuario. |
| `negocio` | `Negocio` | Se relaciona con localidad. |
| `categorias` | `Categoria` | Usa nombre como clave. |
| `productos` | `Producto` | Usa nombre como clave. |
| `localidad` | `Localidad` | Se relaciona con provincia. |
| `provincia` | `Provincia` | Contiene las provincias. |
| **A incorporar** | `Venta` | 
| **A incorporar** | `DetalleVenta` |  
| **A incorporar** | `Gasto` |  

`ReporteResumen` es una clase de cálculo; no necesita ser una tabla si el resumen se genera consultando ventas y gastos.

### Posibles ajustes para mantener coherencia

1. Agregar `id_categoria` como clave primaria de `categorias`.
2. Agregar `id_producto` como clave primaria de `productos`.
3. Cambiar `precio` de `VARCHAR` a `DECIMAL(10,2)`.
4. Cambiar `stock` de `VARCHAR` a `INT UNSIGNED`.
5. Usar un tipo de texto para DNI y CUIT, porque pueden contener ceros iniciales y no se utilizan para cálculos.
6. Incorporar las tablas `ventas`, `detalle_venta` y `gastos`.
7. En `detalle_venta`, guardar el precio unitario histórico del producto.

Estos cambios son recomendaciones para el diseño. Deben revisarse en MySQL Workbench antes de implementarlos.

---

## 7. Organización sugerida de archivos Python

Una organización posible del proyecto es:

```text
Cotillon/
│
├── main.py
│
├── modelos/
│   ├── __init__.py
│   ├── usuario.py
│   ├── negocio.py
│   ├── ubicacion.py
│   ├── categoria.py
│   ├── producto.py
│   ├── venta.py
│   ├── detalle_venta.py
│   ├── gasto.py
│   └── reporte_resumen.py
│
├── servicios/
│   ├── __init__.py
│   ├── servicio_autenticacion.py
│   ├── servicio_producto.py
│   ├── servicio_categoria.py
│   ├── servicio_venta.py
│   ├── servicio_gasto.py
│   └── servicio_reporte.py
│
├── repositorios/
│   ├── __init__.py
│   ├── conexion_bd.py
│   ├── usuario_repositorio.py
│   ├── producto_repositorio.py
│   ├── categoria_repositorio.py
│   ├── venta_repositorio.py
│   └── gasto_repositorio.py
│
└── interfaz/
    ├── __init__.py
    ├── pantalla_inicio.py
    ├── pantalla_menu.py
    ├── pantalla_productos.py
    ├── pantalla_categorias.py
    ├── pantalla_ventas.py
    └── pantalla_gastos.py
```

La interfaz se puede implementar con una biblioteca gráfica a elección. La propuesta no obliga a utilizar un framework específico.

---

## 8. Reglas generales de implementación

- Las clases del modelo representan los datos del negocio.
- Los servicios implementan los casos de uso.
- Los repositorios realizan las consultas a Mariadb.
- La interfaz recibe los datos del usuario y muestra resultados.
- No se deben ejecutar consultas SQL directamente desde los botones de la interfaz.
- Antes de registrar una venta se debe verificar el stock de todos sus productos.
- El registro de la venta y la actualización del stock deben confirmarse en una misma transacción.
- Los importes monetarios deben manejarse con `Decimal`, no con `float`.
- Las contraseñas deben almacenarse mediante hashes seguros.
- Las validaciones deben realizarse antes de guardar los datos.

## 9. Alcance de este documento

Este documento define una **propuesta de diseño orientado a objetos**: nombres de clases, atributos, métodos y responsabilidades. No contiene todavía la implementación completa en Python ni las consultas SQL definitivas.

Antes de programar, se deben validar las clases, los permisos de cada tipo de usuario y las relaciones con el modelo de MySQL Workbench junto con el docente.
