./checker -course 'kubernetes' -course-version 'ingresses' -test-suite 'ingress'

minikube addons enable ingress

./deploy_ing

1. Add this line to /etc/hosts:
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