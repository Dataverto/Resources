# Naveda Dataset

Dataset de ejemplo en formato **DuckDB** utilizado en el vídeo:

> **Claude Code + tus datos: guía práctica de Agentic Analytics**

El objetivo de esta base de datos es practicar análisis de datos con Claude Code utilizando un caso realista de negocio.

## Contenido

```
naveda.duckdb
```

La base de datos contiene un escenario ficticio de un eCommerce preparado para investigar preguntas como:

- ¿Por qué han caído las ventas?
- ¿Qué canal está provocando el problema?
- ¿Es un problema de marketing?
- ¿Es un fallo del proceso de compra?
- ¿Qué hipótesis pueden validarse con los datos?

---

# Requisitos

No necesitas instalar PostgreSQL, MySQL ni ningún otro servidor.

Únicamente necesitas **DuckDB**.

## DuckDB CLI

https://duckdb.org/docs/installation/

Una vez instalado:

```bash
duckdb naveda.duckdb
```

## Python

Instala únicamente:

```bash
pip install duckdb
```

Conexión:

```python
import duckdb

con = duckdb.connect("naveda.duckdb")

con.sql("SHOW TABLES")
```

---

# Uso con Claude Code

Una vez abierto el proyecto desde Claude Code puedes comenzar con un prompt como este:

```
Analiza la estructura de naveda.duckdb.

Muéstrame:

- tablas
- columnas
- relaciones
- principales métricas disponibles

No saques conclusiones todavía.
```

Después puedes hacer preguntas de negocio:

```
Las ventas han caído respecto al mes anterior.

Investiga qué ha ocurrido.

No aceptes la primera hipótesis.

Valida cada conclusión mediante consultas SQL y explícame el razonamiento paso a paso.
```

---

# Objetivo

Este dataset está diseñado para practicar **Agentic Analytics**, es decir, utilizar IA para investigar problemas de negocio mediante un proceso iterativo de:

- formular hipótesis
- consultar datos
- validar resultados
- descartar explicaciones incorrectas
- llegar a una conclusión fundamentada

No pretende mostrar únicamente cómo generar SQL, sino cómo construir un flujo de análisis similar al que seguiría un analista de datos.

---

# Vídeo

📺 Claude Code + tus datos: guía práctica

*(Añadir enlace cuando esté publicado.)*

---

# Licencia

Este dataset se proporciona únicamente con fines educativos y de demostración.
