./checker -course 'kubernetes' -course-version 'ingresses' -test-suite 'ingress'

minikube addons enable ingress

1.

kubectl expose deployment aqua --name=aqua-svc --port=80
kubectl expose deployment maroon --name=maroon-svc --port=80
kubectl expose deployment olive --name=olive-svc --port=80

kubectl apply -f .