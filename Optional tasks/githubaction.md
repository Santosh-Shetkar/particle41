## Github Action to Build and Push image to image registry


Using this github workflow you can build images and push it to image registry using github action

.github/workflow

```text
name: build image

on:
  push:
    branches: [ "master" ]

env:
  REGISTRY_SERVER: docker.io
  REGISTRY_NAMESPACE: santosh013
  USER: ${{secrets.USER}}
  PASSWORD: ${{secrets.PASSWORD}}
  REPOSITORY_NAME: simpletimeservice
  TAG: 1.0.1

jobs:

  build:
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v2
    - name: docker login
      run: |
        docker login "${{ env.REGISTRY_SERVER }}" -u "${{ env.USER }}" -p "${{ env.PASSWORD }}"
    
    - name: Build the Docker image
      run: |
        docker build . --tag "${{ env.REGISTRY_SERVER }}"/"${{ env.REGISTRY_NAMESPACE }}"/"${{ env.REPOSITORY_NAME }}":"${{ env.TAG }}"
      
    - name: Docker Push
      run: docker push "${{ env.REGISTRY_SERVER }}"/"${{ env.REGISTRY_NAMESPACE }}"/"${{ env.REPOSITORY_NAME }}":"${{ env.TAG }}"

```