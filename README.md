QWC MapInfo Service
===================

Additional information at a geographic position displayed with right mouse click on map.


Configuration
-------------

The static config files are stored as JSON files in `$CONFIG_PATH` with subdirectories for each tenant,
e.g. `$CONFIG_PATH/default/*.json`. The default tenant name is `default`.

### MapInfo Service config

* [JSON schema](schemas/qwc-mapinfo-service.json)
* File location: `$CONFIG_PATH/<tenant>/mapinfoConfig.json`

Example:
```json
{
  "$schema": "https://raw.githubusercontent.com/qwc-services/qwc-mapinfo-service/master/schemas/qwc-mapinfo-service.json",
  "service": "mapinfo",
  "config": {
    "db_url": "postgresql:///?service=qwc_geodb",
    "info_table": "qwc_geodb.ne_10m_admin_0_countries",
    "info_geom_col": "wkb_geometry",
    "info_display_col": "name",
    "info_title": "Country"
  }
}
```


### Environment variables

Config options in the config file can be overridden by equivalent uppercase environment variables.

| Variable            | Description                  |
|---------------------|------------------------------|
| `INFO_TABLE`        | Table to use                 |
| `INFO_GEOM_COL`     | Geometry column in table     |
| `INFO_DISPLAY_COL`  | Display text column in table |
| `INFO_TITLE`        | Display title                |


Usage
-----

Run as

    python server.py

API documentation:

    http://localhost:5016/api/

Development
-----------

Create a virtual environment:

    virtualenv --python=/usr/bin/python3 .venv

Activate virtual environment:

    source .venv/bin/activate

Install requirements:

    pip install -r requirements.txt

Start local service:

    CONFIG_PATH=/PATH/TO/CONFIGS/ python server.py


Testing
-------

Run all tests:

    python test.py
