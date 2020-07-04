# Wordpress with Persistent volume on K8
## Deployin Wordpress with Persistent Volumes on K8

## Step 1:
* Clone my repository:
``` 
git clone https://github.com/gulsenjm/k8-task.git
```

 ## Step 2: 
* Create persistent volume claims and persistent volume:
``` 
kubectl apply -f mysql-volumeclaim.yaml
```
``` 
kubectl apply -f wordpress-volumeclaim.yaml
```
* Check if pvc is created:
``` 
kubectl get persistentcolumeclaims
```
or
``` 
kubectl get pvc
```

 ## Step 3: 
* Create a secret for mysql password:
``` 
kubectl create secret generic mysql --from-literal=password=YOUR_PASSWORD
```
` NOtE: you can replace "YOUR_PASSWORD" phrase` 

* Deploy mysql:
```
kubectl create -f mysql.yaml
```
* Check if pod is running:
```
kubectl get pods -l app=mysql
```
* Create mysql service:
```
kubectl create -f mysql-service.yaml
```
* Check service:
```
kubectl get service mysql
```

 ## Step 4: 
* Deploy wordpress:
```
kubectl create -f wordpress.yaml
```
* Check if pod is running:
```
kubectl get pods -l app=wordpress
```
* Create wordpress service:
```
kubectl create -f wordpress-service.yaml
```
* Check service:
```
kubectl get svc -l app=wordpress
```
Get the external ip_address and port number and put on browser (like this: 146.85.987.68:80) and you will see your Wordpress Blog page. Ready to set up.

