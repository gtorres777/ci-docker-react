# ci-docker-react

## Description

In this project you can work in a development environment for a frontend worked with React using nginx to enroute the service.<br />
It also contains a github workflow to build and push a docker image that can be run in a production environment

## How to run the different environments?

To be able to run any of the environments you will need `docker` and `docker compose` installed.<br />

## Development environment

It will use the `Dockerfile.dev` file configured in the frontend folder and in the nginx folder.<br />
If you want to change the port where it will be running the service, you can do it in the `docker-compose-dev.yml` file in the nginx service.<br />

In the project directory, you can run:

### `docker compose -f docker-compose-dev.yml up`

Runs the project in development mode.
Open [http://localhost:3050](http://localhost:3050) to view it in the browser.

## Production environment

It will pull the image `biotux7/ci-docker-react:latest` from Dockerhub and run the React production build files that are stored in a nginx running service .<br />
If you want to change the port where it will be running the service, you can do it in the `docker-compose-prod.yml` file in the `nginx_frontend` service.<br />

In the project directory, you can run:

### `docker compose -f docker-compose-prod.yml up`

Runs the project in production mode.
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

## How does the github workflow works?

It has 2 jobs that will run when a change is pushed to the `main` branch of the repository, the first one will build a test image where it can run the tests for the React app and once it
finishes successfully it will run the other job where it will build an image with the production files from React, integrate this ones into a nginx service and push the image to Dockerhub
