# docker-Java-kubernetes-project
Deploying Java Applications with Docker and Kubernetes

Credit: https://github.com/danielbryantuk/oreilly-docker-java-shopping/

1) Go to Each Micro services like productcatalogue, shopfront, stockmanager
2) As this is Maven repo we have to build the code and generate the jar or artifactory then after that using docker we are generating the image for the artifactory
mvn clean install
mvn clean package
mvn clean test -DargLine="--add-opens java.base/java.lang=ALL-UNNAMED"
after runnning the above commands a target folder will be created in which the snapshot jar is present.
we are making this jar as a image and pushing to docker hub.
docker build -t anudeep0496/shopfront:v1 .
docker build -t anudeep0496/productcatalogue:v1 .
3) This is image is being pushed to Docker hub. <br>
docker push anudeep0496/shopfront:v1 <br>
docker push anudeep0496/productcatalogue:v1<br>
4) This image is used in each and every kubernetes yaml files respectively.

Before starting the minikube make sure the docker is being up and running
To start the minikube:
1) minikube start

Go to kubernetes folder
run the below commands

To apply the service and deployment yaml of the services:<br>
1)kubectl apply -f shopfront-service.yaml<br>
2)kubectl apply -f productcatalogue-service.yaml<br>
3)kubectl apply -f stockmanager-service.yaml --> this will not work because there is some pom depencides issues are present<br>

To delete the services<br>
1)kubectl apply -f stockmanager-service.yaml --force<br>
2)kubectl delete -f stockmanager-service.yaml<br>

To check the Endpoint Url of the service<br>
1)minikube service shopfront<br>
2)minikube service productcatalogue<br>

End point Url's will be:<br>
1)shopfront : http://127.0.0.1:55885/ <br>
2)productcatalogue : http://127.0.0.1:56146/products <br>


<H2> Git History Commands </H2>
    git init <br>
    git branch <br>
    git add . <br>
    git status <br>
    git commit -m "Initial commit of docker-Java-kubernetes-project" <br>
    git status <br>
    git remote add https://github.com/Anudeep0496/docker-Java-kubernetes-project.git <br>
    git push -u origin main <br>
    git remote -v <br>
    git remote remove origin <br>
    git remote -v <br>
    git remote add https://github.com/Anudeep0496/docker-Java-kubernetes-project.git <br>
    git remote -v <br>
    git init <br>
    git remote -v <br>
    git remote add origin https://github.com/Anudeep0496/docker-Java-kubernetes-project.git <br>
    git remote -v <br>
    git push -u origin main <br>
