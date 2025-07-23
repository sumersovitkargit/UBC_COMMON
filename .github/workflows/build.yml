name: CI/CD Pipeline

on:
  workflow_dispatch:
    inputs:
      environment-name:
        description: 'Choose environment'
        type: choice
        required: true
        options: [java, python]

jobs:
  build-java:
    if: ${{ github.event.inputs.environment-name == 'java' }}
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Java repo
        uses: actions/checkout@v3
        with:
          path: UBS_JAVA

      - name: Set up Docker Buildx
        uses: docker/setup-buildx-action@v2

      - name: Build Java Docker image
        uses: docker/build-push-action@v5
        with:
          context: ./UBS_JAVA
          file: ./UBS_JAVA/Dockerfile
          push: false
          tags: java-image:latest

  build-python:
    if: ${{ github.event.inputs.environment-name == 'python' }}
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Python repo
        uses: actions/checkout@v3
        with:
          path: UBS_Python

      - name: Set up Docker Buildx
        uses: docker/setup-buildx-action@v2

      - name: Build Python Docker image
        uses: docker/build-push-action@v5
        with:
          context: ./UBS_Python
          file: ./UBS_Python/Dockerfile
          push: false
          tags: python-image:latest
