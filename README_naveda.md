Naveda — Dataset

A DuckDB database for a subscription-based coffee DTC business. It contains 12 months of data, approximately 1 million sessions, and around 31,000 orders.

The data is synthetic: it was generated specifically for this livestream and does not come from any real client.

What’s inside

Table	Description
productos	Product catalog, one row per SKU
usuarios	Unique users, acquisition channel, and signup date
sesiones	One row per visit, including channel, device, and user
eventos	Funnel events: product_view → add_to_cart → checkout_start → payment_attempt → purchase
pedidos	One row per order, including revenue, discount, segment, and channel
lineas_pedido	Order lines, including product, quantity, and price
marketing	Daily paid media spend by channel

Quick start

DuckDB does not require a server. It is a single file that can be opened from anywhere.

From the terminal:

# Install the DuckDB CLI:
# https://duckdb.org/docs/installation
duckdb naveda.duckdb
D SELECT count(*) FROM pedidos;
D SELECT canal, count(*) FROM sesiones GROUP BY 1 ORDER BY 2 DESC;

From Python:

import duckdb
con = duckdb.connect("naveda.duckdb", read_only=True)
con.sql("""
    SELECT tipo_evento, count(*)
    FROM eventos
    GROUP BY 1
""").show()

With Claude Code: point your repository to this file and ask questions in natural language.

Build it yourself

The .duckdb file is simply a packaged version of several CSV files. To reproduce it from scratch or modify the dataset, use the generator:

pip install duckdb pandas numpy
python generar_naveda.py        # Creates naveda.duckdb directly

The random seed is fixed, so the output is identical every time.

If you already have the CSV files and only want to create the .duckdb file:

python montar_duckdb.py         # CSV → naveda.duckdb

An honest warning

The data contains intentional noise, including a few null values, duplicate records, and impossible timestamps.

It also contains three hidden findings.

I will not tell you what they are. The point is to discover them and, above all, validate that the output produced by your tool is actually correct.
