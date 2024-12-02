# compose-exercise-foodtruck

SF Food Trucks

> San Francisco's finger-licking street food now at your fingertips.

![img](shot.png)

This is a fun application built with [Flask](http://flask.pocoo.org/) on the backend and [Elasticsearch](http://elastic.co/) is the search engine powering the searches. The front-end is built with [React](http://facebook.github.io/react/) and the beautiful maps are courtesy of [Mapbox](https://www.mapbox.com/).

The data for the food trucks is made available in the public domain by [SF Data](https://data.sfgov.org/Economy-and-Community/Mobile-Food-Facility-Permit/rqzj-sfat).

## Assignment: Write a `compose.yml` File for the Food Truck App

Develop a `compose.yml` file to deploy a multi-service application. This file will orchestrate an Elasticsearch service and a Flask-based backend service for a food truck search app, ensuring the app builds locally using a provided `Dockerfile`.

## Instructions

1. **Understand the Application Architecture**
   - The application consists of the following services:
     - **Elasticsearch (Search Engine):**
       - Used to index and search food truck data.
       - Runs as a single-node instance.
       - Exposes port `9200` for communication.
       - Uses a named volume to persist data.
     - **Flask Backend (API):**
       - Handles the API logic for the food truck search.
       - Built from a `Dockerfile` in the current directory.
       - Depends on Elasticsearch for data.
       - Runs on port `5000`.
       - Uses a local directory to store its code for development.

2. **Compose File Requirements**
   - Your `compose.yml` file should:
     - Define the Elasticsearch service:
       - Use the image `docker.elastic.co/elasticsearch/elasticsearch:6.3.2`.
       - Set the `discovery.type=single-node` environment variable.
       - Map port `9200` to the host machine.
       - Persist data using a named volume.
     - Define the Flask service:
       - Use the `Dockerfile` in the current directory.
       - Make sure the Elasticsearch service starts first.
       - Map port `5000` to the host machine.
       - Use a volume to persist application source code during development.

3. **Steps to Complete**
   - Create a `compose.yml` file in the project directory.
   - Test your configuration by running:
     ```bash
     docker compose up
     ```
   - Verify the following:
     - Elasticsearch is accessible on `http://localhost:9200`.
     - The Flask API is accessible on `http://localhost:5000`.
     - No errors appear in the container logs.
