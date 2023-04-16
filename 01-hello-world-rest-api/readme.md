# Hello World Rest API docker image creation and deploying to the cluster in Google Cloud using GKE

### Running the Application
### Prerequisites
1. Install Docker Desktop
2. Have an account on https://hub.docker.com/
3. Have an account on Google cloud

Run RestfulWebServicesApplication as a Java Application.

The below plugin will create the docker image and push in the docker hub

<plugin>
        <groupId>com.spotify</groupId>
        <artifactId>dockerfile-maven-plugin</artifactId>
        <version>1.4.6</version>
        <executions>
            <execution>
                <id>default</id>
                <goals>
                    <goal>build</goal>
                    <!-- <goal>push</goal> -->
                </goals>
            </execution>
        </executions>
        <configuration>
            <repository>ahamadfaiz7/${project.name}</repository>
            <tag>${project.version}</tag>
        </configuration>
</plugin>

### From Docker Desktop push the docker image to Docker Hub
## Create the cluster on Google cloud 
### Run the below Kubernetes commands to deploy the image to Google cloud cluster

kubectl create deployment faiz-hello-world-rest-api --image=ahamadfaiz7/hello-world-rest-api:0.0.4-SNAPSHOT
kubectl expose deployment faiz-hello-world-rest-api --type=LoadBalancer --port=8080

### Accessing the endpoint for spring boot application on localhost 
 Localhost : http://localhost:8080/hello-world

### Accessing the endpoint for spring boot application on Google cloud
http://34.72.122.254:8080/hello-world


```json
{"message":"Hello World"}
```