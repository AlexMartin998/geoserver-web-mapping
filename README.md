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
