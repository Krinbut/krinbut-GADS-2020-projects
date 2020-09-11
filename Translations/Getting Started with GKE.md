# Google Cloud Fundamentals: Getting Started with GKE

Objectives

- Provision a Kubernetes cluster using Kubernetes Engine.

- Deploy and manage Docker containers using kubectl

## Task 2: Confirm that needed APIs are enabled

- Set Default project

        gcloud config set project MY_PROJECT_ID

- Get list of services that are enabled

        gcloud services list --available

- Enable Service if not-Enabled

        gcloud services enable SERVICE_NAME

## Task 3: Start a Kubernetes Engine cluster

- Place ZONE in an environment variable for convinience

        export MY_ZONE=us-central1-a

- Start a Kubernetes cluster managed by Kubernetes Engine. Name the cluster webfrontend and configure it to run 2 nodes:

        gcloud container clusters create webfrontend --zone $MY_ZONE --num-nodes 2

- check your installed version of Kubernetes

        kubectl version

- View your running nodes

        gcloud container clusters list

## Task 4: Run and deploy a container

- launch a single instance of the nginx container. (Nginx is a popular web server.)

        kubectl create deploy nginx --image=nginx:1.17.10

- View the pod running the nginx container:

        kubectl get pods

- Expose the nginx container to the Internet:

        kubectl expose deployment nginx --port 80 --type LoadBalancer

- view the new service

        kubectl get services

- TEST external IP on CLI to confirm it can be reached from any browser

        curl http://34.123.187.13:80

## END LAB