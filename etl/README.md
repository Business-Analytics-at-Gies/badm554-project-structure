# etl/

The queries (or notebook) that build your tables, run in order with no manual fixes. Number the files so the order
is obvious, for example:

1. `01_clean_sales.sql`: a **view** that picks the columns you need, fixes types and names, and **fixes the date
   range** (for example 2022-01-01 to 2025-12-31), so your counts do not change when the public data adds new
   months.
2. `02_dim_store.sql`, `03_dim_date.sql`, and so on: your dimension **tables**, built with `CREATE OR REPLACE TABLE`.
3. `04_fact_sales.sql`: your fact table, at the grain stated in `docs/schema.md`.
4. A last step that prints the row count of every table, so you can compare with `warehouse/README.md`.

`CREATE OR REPLACE` means running everything a second time gives the same row counts as the first.

Each teammate can own some of these files. Your commits show your part, and that is what you explain at your
defense. Anyone on the team should be able to run all of them.

**One notebook is fine too:** put the same steps in order as notebook cells, with a short comment above each. DuckDB teams work this way; say at the top which files in `data/` the notebook expects and what it builds.
