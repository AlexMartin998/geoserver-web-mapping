# Web Mapping Application

## Features

⚡️ GeoServer\
⚡️ PostgreSQL\
⚡️ OpenLayers\
⚡️ HTML5, CSS3 and JS\
⚡️ Dockerized app

## Running the app with Docker

Create `.env` based on `.example.env`

```
touch .env
```

Running the app with docker

```bash
# create data/
mkdir data

# build and run containers
docker compose up --build
```

In a web browser, navigate to `http://localhost:8080/geoserver`

## Importing shapefiles into PostgreSQL

Make sure that the database already has the PostGIS extension installed.

```bash
# table must not exist
docker exec -i postgresdb shp2pgsql -I -s 4326 `/path-in-container` geoserver.gis | docker exec -i postgresdb psql -U `user` -d `db`

# another option: table name will be provided by shp metadata
docker exec -i postgresdb shp2pgsql -s 4326 -I -D -W "LATIN1" `/path-in-container` | docker exec -i postgresdb psql -U `user` -d `db`
```

In addition, you can create an sql file to manually insert the data into Postgres.

```bash
# Create sql file
docker exec -i postgresdb shp2pgsql -G -I  `/path-in-container` geoserver.gis > ./data.sql | docker exec -i postgresdb psql -U `user` -d `db` -f ./data.sql
```
