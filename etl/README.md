# etl/

The notebook that builds your warehouse, run top to bottom with no manual fixes. Suggested sections, in order:

1. **Extract**: open the source read-only and copy it as it is.
2. **Transform**: build the dimensions and the fact table at the grain stated in `docs/schema.md`; give the
   warehouse its own keys.
3. **Load**: write the tables into `warehouse/<name>.duckdb`, starting from a known state so a second run gives the
   same row counts as the first.
4. **Validate**: run the checks in `validation/` or call them from here, and print row counts in and out.

Say at the top of the notebook which files in `data/` it expects and what it produces.
