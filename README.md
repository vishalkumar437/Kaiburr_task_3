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