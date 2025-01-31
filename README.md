# optum-azure-ms - Training Rough notes for reference
DEV OPS:
http://dev.azure.com

az aks get-credentials --resource-group demo-rg-04 --name demo-aks-04-2 - command to merge the azure crdentails to Kubernetes

kubectl create deployment greet-service --image=suryamnaidu1985/greet-service:1.0 --port=8080 - to deploy the public image from docker hub hosted imaged in kubernetes

kubectl scale deployment greet-service --replicas=3

kubectl get pods --watch

kubectl expose deployment greet-service --type=LoadBalancer --port=8181 --target-port=8080

kubectl get svc

kubectl delete svc greet-service

kubectl get deployment greet-service -o yaml

TRAINING URLS AND LAB Repos git Links:
https://github.com/Suryam1985/cloud-app
https://github.com/sbtalk71/cloud-app
https://github.com/Suryam1985/optum-azure-training

user04@sbtalkhotmail.onmicrosoft.com

Micro@8559

https://azcliprod.blob.core.windows.net/msi/azure-cli-2.68.0-x64.msi

http://portal.azure.com/


**Docker commands:**
docker build -t suryamnaidu1985/greet-service:1.0 .

docker run --rm --name greeter -p 8090:8080 sbtalk71/greet-service:1.0

Docker push suryamnaidu1985/greet-service:1.0

management:

 endpoints:

   web:

     exposure:

       include: "*"

 endpoint:

   health:

     show-details: always

<dependency>

<groupId>org.springframework.boot</groupId>

<artifactId>spring-boot-starter-aop</artifactId>

</dependency>


resilience4j.circuitbreaker:

  instances:

    orderBackend:

      registerHealthIndicator: true

      slidingWindowSize: 10

      permittedNumberOfCallsInHalfOpenState: 3

      slidingWindowType: COUNT_BASED

      minimumNumberOfCalls: 3

      waitDurationInOpenState: 5s

      failureRateThreshold: 50

      eventConsumerBufferSize: 10

      automaticTransitionFromOpenToHalfOpenEnabled: true



FROM amazoncorretto:21-alpine3.20-jdk

 EXPOSE 8080

 COPY target/*.jar /home/app.jar

 WORKDIR /home/

 CMD java -jar app.jar
