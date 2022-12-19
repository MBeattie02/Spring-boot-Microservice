# Docker

## Images

- Currency Exchange Service
  - v11 - mabeatti/mmv2-currency-exchange-service:0.0.11-SNAPSHOT
  - v12 - mabeatti/mmv2-currency-exchange-service:0.0.12-SNAPSHOT
- Currency Conversion Service
  - mabeatti/mmv2-currency-conversion-service:0.0.11-SNAPSHOT
    - Uses CURRENCY_EXCHANGE_SERVICE_HOST
  - mabeatti/mmv2-currency-conversion-service:0.0.12-SNAPSHOT
    - Uses CURRENCY_EXCHANGE_URI

## URLS

#### Currency Exchange Service

- http://localhost:8000/currency-exchange/from/USD/to/INR

#### Currency Conversion Service

- http://localhost:8100/currency-conversion-feign/from/USD/to/INR/quantity/10

#### Commands

```
gcloud container clusters get-credentials mabeatti-cluster --zone us-central1-c --project solid-course-258105
docker login
docker push mabeatti/mmv2-currency-exchange-service:0.0.11-SNAPSHOT
docker push mabeatti/mmv2-currency-conversion-service:0.0.11-SNAPSHOT

kubectl create deployment currency-exchange --image=mabeatti/mmv2-currency-exchange-service:0.0.11-SNAPSHOT
kubectl expose deployment currency-exchange --type=LoadBalancer --port=8000
kubectl get svc
kubectl get services
kubectl get pods
kubectl get po
kubectl get replicaset
kubectl get rs
kubectl get all

kubectl create deployment currency-conversion --image=mabeatti/mmv2-currency-conversion-service:0.0.11-SNAPSHOT
kubectl expose deployment currency-conversion --type=LoadBalancer --port=8100

kubectl get svc --watch

kubectl get deployments

kubectl get deployment currency-exchange -o yaml >> deployment.yaml
kubectl get service currency-exchange -o yaml >> service.yaml

kubectl diff -f deployment.yaml
kubectl apply -f deployment.yaml

kubectl delete all -l app=currency-exchange
kubectl delete all -l app=currency-conversion

kubectl rollout history deployment currency-conversion
kubectl rollout history deployment currency-exchange
kubectl rollout undo deployment currency-exchange --to-revision=1

kubectl logs currency-exchange-9fc6f979b-2gmn8
kubectl logs -f currency-exchange-9fc6f979b-2gmn8

kubectl autoscale deployment currency-exchange --min=1 --max=3 --cpu-percent=5
kubectl get hpa

kubectl top pod
kubectl top nodes
kubectl get hpa
kubectl delete hpa currency-exchange

kubectl create configmap currency-conversion --from-literal=CURRENCY_EXCHANGE_URI=http://currency-exchange
kubectl get configmap

kubectl get configmap currency-conversion -o yaml >> configmap.yaml

watch -n 0.1 curl http://34.66.241.150:8100/currency-conversion-feign/from/USD/to/INR/quantity/10

docker push mabeatti/mmv2-currency-conversion-service:0.0.12-SNAPSHOT
docker push mabeatti/mmv2-currency-exchange-service:0.0.12-SNAPSHOT
```
