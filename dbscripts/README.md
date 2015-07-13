# Database Setup

## Dependencies

Before running the `Makefile` make sure you have the following installed:
- Postgres 9.0+ and PostGIS 2.1.7+
- R 3.1.2
- ogr2ogr
- tippecanoe

## Installing

The scripts here expect that the `data/` directory contains:

 - The gzipped CSV files of the [summary data](../summaries/README.md), as produced by the data processing scripts.
  - `states-months/`: monthly state data
  - `districts`: monthly districts data
 - `DISTRICT_11.*`: the 2011 India district boundaries shapefile from MLInfo
 - `UD_vills_CCODE01.csv`: Data from the RGGVY program
 - `villages.csv`: Villagecodes and associated lat,lon

To run all the database scripts run `make DATABASE_URL=$DATABASE_URL`

Commands:
- `make boundaries *`: calls the following
  - `make csv_boundaries`: create the CSV files for districts and states
  - `make boundaries_import *`: creates the DB tables and imports
  - `make boundaries_index *`: creates the tables index
- `make villages * `:
  - `make villages_import * `: imports villages.csv and parallel streams the village montly data
  - `make villages_indes * `: build the villages tables index
- `make rggvy * `: creates rggvy.csv, the rgvy table and imports it
- `make sample`: Create vector tiles
- `make clean`:
  - `make clean_boundaries`: remove boundaries csvs and deps
  - `make clean_rgvy`: remove rggvy csvs and deps


 `*`: takes `DATABASE_URL` as an argument

