# OCHA Centre for Humanitarian Data — Data Science Team Claude Config

## Data loading/saving
### `ocha-stratus`
Use `ocha-stratus` for all blob storage and database access. Don't read from blob directly with raw Azure SDK calls.

```python
import ocha_stratus as stratus

blob_name = f"{PROJECT_PREFIX}/example_blob"
df_example = stratus.load_parquet_from_blob(blob_name)
```

Check the stratus docs/README for current auth and init patterns — don't guess.

### Blob storage naming
Follow this convention for all storage paths:
```
{PROJECT_PREFIX}/{raw|processed}/{datasource}/{filename}
```
- `PROJECT_PREFIX` comes from `src.constants`
- `raw/` for unmodified source data, `processed/` for anything derived
- `datasource` matches the source name (e.g. `chirps`, `seas5`, `ibtracs`)
- Filenames should be descriptive and include relevant date/version info where applicable

Example: `ds-aa-bfa-drought/processed/seas5/2024-03_tercile_probs.nc`

## Data processing

### `ocha-lens`
- Try to use `ocha-lens` for common data processing operations before writing custom logic. It may already have what you need.

### General
- `xarray` for gridded data, `geopandas` for vector
- CRS is always EPSG:4326 unless explicitly noted
- Use `rioxarray` for raster I/O and clipping
- Generally, we use a leadtime convention for months such that adding the issued time and leadtime produces the valid time. So, a forecast issued in March, with a leadtime of 1 month, would be valid for April.

## Variable/key naming

- Use `valid_time` for the valid time of the forecast (or `valid_date`). Sometimes this is referred to as the "reference time" or simply the "time".
- Use `issued_time` for the issued time or publication time of the forecast.
- If the data is observational, use `valid_time`.

## Python conventions
- Python 3.11+. Use `uv` for environment management, not pip directly.
- Type hints on all function signatures
- f-strings for string formatting
- Don't suppress exceptions silently — log or re-raise

## Project structure
Projects typically use a local `src` package. Common layout:
```
src/
  constants.py      # PROJECT_PREFIX and other project-wide constants live here
  datasources/      # One module per data source (e.g. chirps.py, seas5.py)
  utils/            # Shared helpers
```
This is a guide not a rule — check the project's actual structure before assuming it.
`PROJECT_PREFIX` should always come from `src.constants`, never hardcoded inline.

## Data sources
TBD

## Documentation
TBD
