## Cansary with kubernetes
```bash
cd TP_Canary
minikube start
minikube addons enable ingress
minikube addons enable ingress
kubectl apply -f deployment_main.yaml 
kubectl apply -f deployment_canary.yaml 
kubectl apply -f ingress_main.yaml
kubectl apply -f ingress_canary.yaml
```

![imagen1](images/image.png)

```bash
kubectl get ing
```

![imagen2](images/image-2.png)

```bash
for i in $(seq 1 50); do curl -s http://hello-app.local | grep "Hostname"; done | sort | uniq -c

for i in $(seq 1 10); do curl -s http://hello-app.local | grep "Hostname"; done
```

![imagen3](images/image-1.png)

En la imagen anterior se observa que se cumple el 10% del trafico para canary y el 90% para la v1.

## Fuentes:

https://kubernetes.github.io/ingress-nginx/examples/canary/
https://kubernetes.io/docs/concepts/workloads/management/#canary-deployments
https://blog.devops.dev/kubernetes-deployment-strategies-part-2-ec2290717fcb
https://kubernetes.io/docs/concepts/workloads/controllers/deployment/

Video recurso:

https://www.youtube.com/watch?v=DCoBcpOA7W4&t=4648s
