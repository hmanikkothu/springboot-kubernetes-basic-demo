# springboot-kubernetes-basic-demo

``` 
https://spring.io/guides/gs/spring-boot-kubernetes/
```

### Build/Test the app

```
./mvnw install
```

### Build docker image
```
docker build -t localhost/springguides/demo .
```

### Run the container from local registry
```
docker run -p 8080:8080 localhost/springguides/demo
```

### Deploy
Note that the container should specify the 'imagePullPolicy' to 'IfNotPresent' in order to deploy the image from local registry. 

```
kubectl apply -f deployment.yaml 
```

### Verify 

Verify the deployment and the demo service as follows

```
kubectl get all

# Port forward the demo service to localhost in order to access the actuator locally

kubectl port-forward svc/demo 8080:8080

curl http://localhost:8080/actuator
```
