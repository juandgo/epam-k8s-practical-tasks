# As far as now this works in Ubuntu vmware


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

# 3. Editamos el archivo para cambiar el namespace a trouble-1 y aplicamos, de sta forma se crea el trouble1.yaml con el ns trouble-1, para que funcione no deberia estar creado en el directorio, si lo esta solo hay que ejectarlo, pero para este task ya viene creado por defecto por cuando ejecutas el file ./deploy_ing .

sed -i 's/namespace: default/namespace: trouble-1/' trouble1.yaml
kubectl apply -f trouble1.yaml

<!-- MNyfrU1jVnM8PTCR1CTtIC3Gh -->

5.

# Service selectors are wrong / swapped, They are pointing to the opose endpoints, you can see it with the following commands

kubectl describe svc teal-svc -n trouble-2

kubectl describe svc navy-svc -n trouble-2

# Fix teal-svc Selector and targetPort change it to 80

kubectl edit svc teal-svc -n trouble-2

ports:
- port: 80
  protocol: TCP
  targetPort: 80
selector:
  app: teal-color

# Fix navy-svc Selector and targetPort change it to 80
kubectl edit svc navy-svc -n trouble-2

ports:
- port: 80
  protocol: TCP
  targetPort: 80
selector:
  app: navy-color

# Manual Fix ingress, change from port 8080 to 80 of every service

kubectl edit ing trouble-2-ingress -n trouble-2


# 1. Añadir la anotación de rewrite que falta
kubectl annotate ingress trouble-2-ingress -n trouble-2 nginx.ingress.kubernetes.io/rewrite-target=/ --overwrite

# 2. Corregir los puertos en el Ingress para que apunten al 80 del Service, this other way to do it without edit the ingress manualy
kubectl patch ingress trouble-2-ingress -n trouble-2 --type='json' -p='[
  {"op": "replace", "path": "/spec/rules/0/http/paths/0/backend/service/port/number", "value": 80},
  {"op": "replace", "path": "/spec/rules/0/http/paths/1/backend/service/port/number", "value": 80}
]'

# Corregir el Service de Teal, this other way to do it without edit the service manualy
kubectl patch svc teal-svc -n trouble-2 --type='json' -p='[{"op": "replace", "path": "/spec/ports/0/targetPort", "value": 80}]'

# Corregir el Service de Navy, this other way to do it without edit the service manualy
kubectl patch svc navy-svc -n trouble-2 --type='json' -p='[{"op": "replace", "path": "/spec/ports/0/targetPort", "value": 80}]'

<!-- fLHjgfDpPJylQHiArYc1U01ZJ -->

6.