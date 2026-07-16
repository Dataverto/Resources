# Naveda — dataset del directo

Base de datos **DuckDB** de un DTC de café con suscripción. 12 meses, ~1M de sesiones,
~31.000 pedidos. Datos **sintéticos**: generados para este directo, no son de ningún cliente real.

## Qué hay dentro

| Tabla | Qué es |
|---|---|
| `productos` | Catálogo, una fila por SKU |
| `usuarios` | Usuarios únicos, canal y fecha de alta |
| `sesiones` | Una fila por visita (canal, dispositivo, usuario) |
| `eventos` | Embudo: `product_view → add_to_cart → checkout_start → payment_attempt → purchase` |
| `pedidos` | Una fila por pedido (ingresos, descuento, segmento, canal) |
| `lineas_pedido` | Líneas de pedido (producto, unidades, precio) |
| `marketing` | Inversión diaria en paid por canal |

## Uso rápido

DuckDB no necesita servidor. Un solo fichero, se abre desde cualquier sitio.

**Desde la terminal:**
```bash
# instala la CLI de duckdb (https://duckdb.org/docs/installation) y:
duckdb naveda.duckdb
D SELECT count(*) FROM pedidos;
D SELECT canal, count(*) FROM sesiones GROUP BY 1 ORDER BY 2 DESC;
```

**Desde Python:**
```python
import duckdb
con = duckdb.connect("naveda.duckdb", read_only=True)
con.sql("SELECT tipo_evento, count(*) FROM eventos GROUP BY 1").show()
```

**Con Claude Code:** apunta tu repo a este fichero y pregúntale en lenguaje natural.

## Si prefieres montarlo tú

El `.duckdb` es sólo un empaquetado de unos CSV. Si quieres reproducirlo desde cero
(o cambiar algo), tienes el generador:

```bash
pip install duckdb pandas numpy
python generar_naveda.py        # crea naveda.duckdb directamente
```

La semilla está fija, así que sale idéntico cada vez. Si ya tienes los CSV y sólo quieres
el `.duckdb`:

```bash
python montar_duckdb.py         # CSV -> naveda.duckdb
```

## Un aviso honesto

Los datos tienen **ruido a propósito** (algún nulo, algún duplicado, algún timestamp
imposible) y **tres hallazgos escondidos**. No te digo cuáles: la gracia es encontrarlos
y, sobre todo, validar que lo que te devuelva tu herramienta es correcto.
