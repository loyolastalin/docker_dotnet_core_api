  # PODS

  ## 1. Get all the pods in the K8s cluster
  kubectl get pods
  ## 2. Create a pod name with testing and image nginx
  kubectl run testing --image=nginx
  ## 3. Get the pod contians, how many images and the image names
  kubectl descibe pod testing
  ## 4. Create a pod name as redis and wrong image redis123, create a yaml file based on the configuration without executing
  kubectl run redis --image=redis123 --dry-run=client -o yaml > first.yaml
  ### 5. Create the POD
  kubectl apply -f first.yaml
  ### 6. Modify the correct image name of the running pod
  kubectl edit pod redis
  ### 7. Determine the POD running in which node?
  kubectl get pods -o wide
  ### 8. Find the image name of the POD
  kubectl descibe pod testing | grep -i image  

  # Deployment & ReplicaSet ( Rolling updates,undo, pause and resume)
  ## how to create deployment file with name = stalin and image = nginx
  kubectl create deployment stalin --image=nginx --dry-run=client -o yaml > deployment-def.yaml
  ## how to scale replica set as 4
  1. Open the file in editor change the replicas and run the file 
  2. Run the file and scale using scale command => kubectl scale deployment --replicas=4 stalin
  
  # Namespace
  ## Get all the pods in the cluster
  kubectl get ns --no-headers | wc -l
  ## Get all the pods under the research namespace
  kubectl -n research get pods
  ## Create namespece teststalin
  kubectl create ns teststalin
  ## Get pods name blue under which namespace it is available
   kubectl get pods --all-namespaces | grep blue
  ## Gets all the system pods 
  kubectl -n kube-system get pods
  
  
  # Service
  
  ## Get all the service
  kubectl get svc
  ## Create a service for the deployment = simple-webapp-deployment with the Type = NodePort TartgetPort =8080 
  kubectl expose deployment simple-webapp-deployment --name=webapp-service --type=NodePort --target-port=8080 --port=8080 --dry-run=client -o yaml > testing-service.yaml
  ```bash
   1 kubectl get nodes
   2 minikube status
   3 kubectl get deployments
   4 kubectl get services
   5 kubectl get pods
   6 kubectl get pods -o wide
   7 kubectl describe service coretest-network
   8 kubectl get deployments coretest-deployment -o yaml
   9 minikube service coretest-network
   10 kubectl describe pods coretest-deployment-79684f895f-6djss
   11 kubectl get deployments
  12 kubectl get services
  13 kubectl get replicaset
  14 kubectl get secrets
  15 kubectl get ingress
  16 minikube docker-env
  17 minikube -p minikube docker-env | Invoke-Expression
  18 minikube service list
  19 minikube service coretest-network --url
  20 minikube service client-node-port --url
  21 
  ```
