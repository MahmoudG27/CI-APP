# CI/CD pipeline:
1- After developer push code to CI Repository in github.
2- Jenkins CI Pipeline will trigger automatically by Webhook ceated in GitHub Repo to run Jenkinsfile in this repo.
3- Jenkinsfile clone the repo and build the Docker Image and push it to Docker Hub with tag value of variable {BUILD_NUMBER}.
4- Dockerfile makes COPY of Source Code under document root of Nginx.
5- CI Pipeline will pass value of variable {BUILD_NUMBER}.
6- CD Pipeline will be triggered after CI SUCCESS and run Jenkinsfile in CD repo.
7- After Changes the CD repo with New Image in deployment file.
8- ArgoCD make SYNC automatically to deploy the new manifest file with new Docker Image created from new Code.
9- You can create Argo Application by manifest file (Application.yaml) or Create it manully from Argo Dashboard.
10- The Source of application in Argo is CD repository in GitHub and the destination is Kubernetes Cluster.
# Notes:
If your Jenkins Locally you can Use Ngrok to make Public URL for Jenkins

# CI/CD Project image:

![CI-CD](https://github.com/MahmoudG27/CI-APP/assets/133862420/01cecac8-8396-4424-a404-70a5d74b9b55)

# Delivery Pizza Website

Bake House is a website for Keith Bakery home. It is a specialized pastry shop. It has a wide range from celebration cakes, children cakes, cupcakes, health cakes, .... and more.

### How To Run Website Locally:

In your browser type the website url, or open the terminal and type: 
``` sh
$ google-chrome https://mahaamin.github.io/BakeHouse/index.html
```
To view items in **Our Range** tab you will first need to create some cake-objects to be stored in the local storage:


### Used Technologies:
* HTML5
* CSS
* JavaScript

***

### Contributors:
