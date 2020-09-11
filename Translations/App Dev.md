# App Dev: Setting up a Development Environment v1.1

## Objectives

In this lab, you will learn how to perform the following tasks:

    - Provision a Google Compute Engine instance.
    - Connect to the instance using SSH.
    - Install software on the instance.
    - Verify the software installation.

## Steps

1. Provision a Google Compute Engine instance, Allow full access to all cloud API, Allow HTTP traffic

    gcloud compute instances create dev-instances --zone=us-central1a --subnet default --scopes=https://www.googleapis.com/auth/cloud-platform --tags http

    gcloud compute firewall-rule create allow-http --action=ALLOW --destination=INGRESS --rules=tcp:80 --target-tags=http

2. Connect to the instances using SSH

    gcloud compute SSH dev-instances

3. Install software on the VM Instance

A. In the SSH session, to update the Debian package list, execute the following command:

    sudo apt-get update

B. To install Git, execute the following command:

    sudo apt-get install git

C. To download the Node.js setup script, execute the following command:

    curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -

D. To install npm and Node.js, execute the following command:

    sudo apt install nodejs

4. Configure the VM to Run Application Software
    In this section, you will verify the software installation and run some sample codes.

A. To check the version of Node.js, execute the following command:

    node -v

B. To clone the class repository, execute the following command:

    git clone https://github.com/GoogleCloudPlatform/training-data-analyst

C. To change the working directory, execute the following command:

    cd ~/training-data-analyst/courses/developingapps/nodejs/devenv/

D. To run a simple web server, execute the following command:

    sudo node server/app.js

E. Test external IP (34.66.255.128) for server on CLI using the curl command

    curl http://34.66.255.128 

You should see a Hello GCP dev! message from Node.js.

F. Press Ctrl+C to stop application

G. To install the Node.js library for Compute Engine, execute the following command:

    npm install

H. To run a simple Node.js application that lists Compute Engine instances, execute the following command:

    node list-gce-instances.js

## END SESSION
