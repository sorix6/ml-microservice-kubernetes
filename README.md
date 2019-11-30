[![CircleCI](https://circleci.com/gh/sorix6/ml-microservice-kubernetes/tree/master.svg?style=svg)](https://circleci.com/gh/sorix6/ml-microservice-kubernetes/tree/master)

## Project Overview

This project consists in operationalizing a Machine Learning Microservice API based on a Python flask-app.

### Project Tasks

The project goal is to operationalize this working, machine learning microservice using [kubernetes](https://kubernetes.io/), which is an open-source system for automating the management of containerized applications. This project will cover:
* Testing the code using linting
* Completing a Dockerfile to containerize this application
* Deploying the containerized application using Docker and making a prediction
* Improving the log statements in the source code for this application
* Configuring Kubernetes and creating a Kubernetes cluster
* Deploying a container using Kubernetes and making a prediction
* Uploading a complete Github repo with CircleCI to indicate that the code has been tested

---

## Setup the Environment

* Create a virtualenv and activate it
* Run `make install` to install the necessary dependencies

### Running `app.py`

1. Standalone:  `python app.py`
2. Run in Docker:  `./run_docker.sh`
3. Run in Kubernetes:  `./run_kubernetes.sh`

### Uploading the Docker image

To upload the image to Docker Hub: `./upload_docker.sh`

*Note that running this script will prompt for the username and password of the Docker account.*

### Kubernetes Steps

* Setup and Configure Docker locally
* Setup and Configure Kubernetes locally 
    - `minikube start` to start a local cluster
    - `kubectl config view` to check that the cluster has been started (there should be least one cluster with a certificate-authority and server)
* Create Flask app in Container and run via kubectl `./run_kubernetes.sh`

* After you’re are done deploying the containerized application and making test predictions via Kubernetes cluster, you should clean up your resources and delete the kubernetes cluster with a call to `minikube delete`

### Files

* `output_txt_files/docker_out.txt` containes the prediction returned after running the app with Docker

* `output_txt_files/kubernetes_out.txt` containes the prediction returned after running the app with Kubernetes

* `run_docker.sh` contains the steps to get Docker running the app locally:
    - Build the image and add a descriptive tag
    - Run flask app

* `run_kubernetes.sh` contains the steps to get Kubernetes running the app locally:
    - Run the Docker Hub container with kubernetes
    - Forward the container port to a host

* `upload_docker.sh` contains the steps to upload the image to the Docker repository:
    - Authenticate & tag the image
    - Push image to a docker repository