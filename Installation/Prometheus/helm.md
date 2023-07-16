# Install using Helm

## Add helm repo

`helm repo add prometheus-community https://prometheus-community.github.io/helm-charts`

## Update helm repo

`helm repo update`

## Install helm 

`helm install prometheus prometheus-community/prometheus`

## Expose Prometheus Service

This is required to access prometheus-server using your browser.

`kubectl expose service prometheus-server --type=NodePort --target-port=9090 --name=prometheus-server-ext`


=================================

https://www.youtube.com/watch?v=vC7CG2ONjGM

Add metrix server 

kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/download/v0.4.3/components.yaml

#Use the following command to verify that the metrics-server deployment is running the desired number of pods:
kubectl get deployment metrics-server -n kube-system

kubectl get pods -n kube-system

#Confirm Metrics server is active.
kubectl get apiservice v1beta1.metrics.k8s.io -o yaml

#Metrics API can also be accessed by using the kubectl top command.
#To display cluster nodes resource usage – CPU/Memory/Storage you’ll run the command:
kubectl top nodes

#Similar command can be used for pods.
kubectl top pods -A

#You can also access use kubectl get –raw to pull raw resource usage metrics for all nodes in the cluster.
kubectl get --raw "/apis/metrics.k8s.io/v1beta1/nodes"
