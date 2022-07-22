#!/usr/bin/env bash

# Build image
docker build --tag=api .

# List docker images
docker image ls

# Run flask app
docker run -p 8000:5001 api

# Tips
# Below are potential options for building and running your container.
# To build your container, if tagging your container as my-python-app:
docker build -t my-python-app .

# To run the container, given my-python-app as the image tag and my-running-app as the container name:
docker run -it --rm --name my-running-app my-python-app
