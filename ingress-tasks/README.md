./checker -course 'kubernetes' -course-version 'ingresses' -test-suite 'ingress'

minikube addons enable ingress

./deploy_ing

1. 

# Add this line to /etc/hosts:
127.0.0.1 trouble-1.k8slab.net trouble-2.k8slab.net trouble-3.k8slab.net aqua.k8slab.net maroon.k8slab.net olive.k8slab.net colors.k8slab.net


kubectl apply -f .

sudo fuser -k 80/tcp


sudo KUBECONFIG=$HOME/.kube/config kubectl port-forward --address 127.0.0.1 -n ingress-nginx service/ingress-nginx-controller 80:80

Probe:
curl -I http://maroon.k8slab.net

<!-- paROpZ8Knn1FSnoeiNY0XhOac -->

2.

kubectl apply -f colors-ingress.yml 

<!-- m6hOzMskF2E5qxUwFNdJ4Nd7F -->

3.

kubectl apply -f ./task3

<!-- 673XzDdBflrUhn66MycthKfV2 -->

4.

kubectl get ing -A

# 1. Guardamos la configuración actual en un archivo
kubectl get ingress trouble-1-ingress -n default -o yaml > trouble1.yaml

# 2. Borramos el original que causa el conflicto
kubectl delete ingress trouble-1-ingress -n default

# 3. Editamos el archivo para cambiar el namespace a trouble-1 y aplicamos
sed -i 's/namespace: default/namespace: trouble-1/' trouble1.yaml
kubectl apply -f trouble1.yaml

<!-- MNyfrU1jVnM8PTCR1CTtIC3Gh -->