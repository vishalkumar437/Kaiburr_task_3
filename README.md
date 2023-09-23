# TASK 3
# Setting up Docker Containers

## MongoDB
    
### Build MongoDb Image
``` 
       docker build -t mongo-server .
```
```    
       docker run -d -p 27017:27017 --name mongo-server     
```

## Spring Boot
In application.yml define host and port as we define in mongo to connect to application
		
            server:
  			port: 8080
		spring:
  			data:
                mongodb:
                host: mongo-server
                port: 27017
                database: KaiburrAssignment

Make sure to make the jar file of application befor building docker image for the application
    
Build command(I am using Distroless image):

```
docker build -t spring-kaiburr-assignment . 
```
	
Run and Link both the containers

``` Command
  docker run -p 8080:8080 --name spring-kaiburr-assignment --link mongo-server:mongo -d spring-kaiburr-assignment
```

# Kubernetes

## Requirements

    > docker
    > Hyper-v
    > minikube
    > kubectl

### Start minikube with resources

```
    minikube start --memory=2048 --disk-size=10g
```

### Creating Pods

```
    kubectl create -f "mongodeployment.yml"
    kubectl create -f "springdeployment.yml"
```
![Screenshot 2023-09-23 233135.png](..%2FScreenshots%2FScreenshot%202023-09-23%20233135.png)
### Used NodePort to expose port to 30100 for Spring application

## ScreenShots

### Services for mongo and API

![Screenshot 2023-09-24 003029.png](..%2FScreenShots%2FScreenshot%202023-09-24%20003029.png)
### Persistent Volume Claim 

![Screenshot 2023-09-24 003145.png](..%2FScreenShots%2FScreenshot%202023-09-24%20003145.png)

### API on pod details

![Screenshot 2023-09-24 002211.png](..%2FScreenShots%2FScreenshot%202023-09-24%20002211.png)

