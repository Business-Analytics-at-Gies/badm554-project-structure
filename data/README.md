# data/

**Most teams do not need this folder.** If your data is a BigQuery public dataset, your queries in `etl/` read it
directly, and there is nothing to download.

Use this folder only if your team brings its own files (a CSV or Parquet download, for example). The files stay on
each teammate's computer and are **never committed** (this folder is gitignored). Replace this README with
instructions a stranger can follow:

- **What each file is**, and where to download it.
- **How to check you got the right file:** its size or row count, and a checksum.
  On macOS or Linux: `shasum -a 256 <file>`. On Windows PowerShell: `Get-FileHash <file>`.
  If the check fails, download the file again.
