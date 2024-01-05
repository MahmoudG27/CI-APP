# CI/CD pipeline:
* After developer push code to CI Repository in github.
* Jenkins CI Pipeline will trigger automatically by Webhook ceated in GitHub Repo to run Jenkinsfile in this repo.
* Jenkinsfile clone the repo and build the Docker Image and push it to Docker Hub with tag value of variable {BUILD_NUMBER}.
* Dockerfile makes COPY of Source Code under document root of Nginx.
* CI Pipeline will pass value of variable {BUILD_NUMBER}.
* CD Pipeline will be triggered after CI SUCCESS and run Jenkinsfile in CD repo.
* After Changes the CD repo with New Image in deployment file.
* ArgoCD make SYNC automatically to deploy the new manifest file with new Docker Image created from new Code.
* You can create Argo Application by manifest file (Application.yaml) or Create it manully from Argo Dashboard.
* The Source of application in Argo is CD repository in GitHub and the destination is Kubernetes Cluster.
# Notes:
* If your Jenkins machine doesn't Public IP and you need make WebHook. You can use Ngrok to make Public URL for Jenkins or any App

***

# CI/CD Project image:

![CI-CD](https://github.com/MahmoudG27/CI-APP/assets/133862420/01cecac8-8396-4424-a404-70a5d74b9b55)

***

# Delivery Pizza Website



### How To Run Website Locally:

In your browser type the website url, or open the terminal and type: 
``` sh
$ google-chrome https://mahmoudg.github.io/Delivery-pizza/index.html
```

### Used Technologies:
* HTML5
* CSS
* JavaScript

***

## Contributors:
* Developer
|[Ahmed Soliman](https://github.com/solman500)|
* DevOps Engineer
|[Mahmoud Gamal](https://github.com/MahmoudG27)|
