# Global Oil Infrastructure Tracker (GOIT)

Project with [Global Energy Monitor](https://globalenergymonitor.org), based on previous trackers, specifically the more recent 2022 trackers (Asia Gas Tracker, Wind Tracker)

Quickbooks: "CoalSwarm:Trackers 2022-A"

* Point based with clustering (though no point based data are present at the moment)
* Lines for pipelines
* Status and type filters 
* Support for URL parameters 

## Hosting

Unknown. Likely via an iframe embedded in a WordPress page    

GH pages link: https://greeninfo-network.github.io/global-oil-infrastructure-tracker/

## Development

Pre-requisites:
* Node (>=18.0.0), npm (>=8.6.0), nvm (>= 0.39.1)

To match the development node version:
```bash
nvm use
```

To install required packages (first time only on a new machine):
```bash
npm install
```

To start a development server on `localhost:2186` and watch for changes:
```bash
npm run start
```

## Production
```bash
# build to the docs directory and commit to `main`
npm run build
```
The app is hosted on GitHub pages (via the `docs/` folder).

## Data Management

There are two primary sources
* Country boundaries (see the `documentation/update_country_geojson` directory for details)
* A single Google spreadhsheet is used to manage data. 
https://docs.google.com/spreadsheets/d/1OysHd1cBjVN98ufNEDIwtI8Du3hY7hm8-wfpYk7wRDE/edit

## Data update

1. Typically the client will email a link to a spreadsheet with data. Manually copy that sheet onto a temporary sheet, check that the column headings match, and then copy over the `raw_data` sheet. From there, check the formulas in the first row of all cols in data_export tab to ensure that the data is being copied/incorporated correctly
1. Save the [data_export tab](https://docs.google.com/spreadsheets/d/1OysHd1cBjVN98ufNEDIwtI8Du3hY7hm8-wfpYk7wRDE/edit#gid=997296159) as `data/data.csv`
2. On major updates, run `documentation/update_country_geojson/make_countries_json.py` to capture boundaries for new countries that may have been added.

