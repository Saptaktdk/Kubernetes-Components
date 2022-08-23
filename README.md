
![](/Kubernetes-logo.png)


## Kubernetes Components:
## 1.Node and Pods
* Nodes contain the necessary services to run Pods. 
* Pod is the smallest unit of Kubernetes. 
* It is an abstraction over a container.
* Generally , one application is assigned to each pod.
* Kubernetes offers virtual network , i.e each pod is given an IP address.This way the Pods
  can communicate with each other.

* If a pod gets destroyed, then it gets a new IP address on recreation.
  

## 2.Service and Ingress
* A service is a static/permanent IP address with a DNS name that can be assigned to each pods.
* Say, I have 2 pods in a working node, application and database pod.So, there services will be different from 
  each other.
* If a pod dies, the service of the pod will still remain same.
* There are 2 types of services: External and Internal service.
* External services are the services that creates a communication with an external source.
  Say, you want your application to be accesible through a browser, for that you need external
  services.

* But you don't want your database to go public.For that you will create an internal service.
* The urls of external services are not very safe.It looks like this: http://my-app-service-ip:port
* It should be like http://my-app.com
* For that Ingress is used.
* Ingress is an API object that provides routing rules to manage external users' access to the services in a
  Kubernetes cluster, typically via HTTPS/HTTP.

## 3.ConfigMap and Secret
* ConfigMap is external configuration of your application.
* It usually contains configuration data like urls of database.
* Pods are connected to the ConfigMap so that it gets the data.
* Username and passwords can also be added to ConfigMap, but it will be insecure .
* So, for that we use Secret component. 
* Secret is used to store secret data.It stores data in base64 encoded format. 
* They are connected to pods simiar to ConfigMap, so that pods get the data.

## 4.Volumes
* If a pod restarts or stops, the data inside it will be gone foreveer.For that volumes are used.
* They are used for data persistence.
* It basically attaches a physical storage on a hard drive to your pod.
* This storage can either  be on the same server node or on a remote storage i.e outside
  of the k8s cluster.
  
## 5.Deployment and StatefulSet
* Let's say you have a working node that contains 2 pods, application and database pods.
* Suppose the  application pod dies or crushes or you have to restart the pod.
* In that case , a user would not be able to reach the application, which is bad in production.
* We can avert this crisis by replicating all the informations to another or multiple servers.
* So, we will have another node where the clone of our application will run.
* The clone will also be connected to the same service. 
* To create the clone we don't need to create or build new pod,instead we can define a 
  blueprint of the application pod.
* That blueprint is known as Deployment.
* So everytime a pod dies, we use deployments to clone the pod.
* However database cannot be replicated via deployment.
* The replicating mechanism is offered by the component StatefulSet.
* It's meant specifically for applications like databases.
