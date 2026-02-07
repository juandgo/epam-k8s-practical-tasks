./checker -course 'kubernetes' -course-version 'services' -test-suite 'service'

1. Create pod-info-svc service for pod-info-app deployment:

kubectl get deploy pod-info-app -o yaml

k apply -f pod-info-svc.yml

<!-- 0RAOI4tCTG3q5ALK7mF0Y4GbB -->

2. Run a busybox pod

kubectl run test --rm -it --image=busybox --restart=Never -- sh

wget -q -O- pod-info-svc

exit 

kubectl run test --rm -it --image=busybox --restart=Never -- \
wget -q -O- pod-info-svc > $HOME/testing-clusterip-web.log

kubectl run test --rm -it --image=busybox --restart=Never -- \
nslookup pod-info-svc > $HOME/testing-clusterip-nslookup.log

ls -l $HOME/testing-clusterip-*.log

<!-- 0RAOI4tCTG3q5ALK7mF0Y4GbB -->

2.

<!-- 2ZcpFkP7mqZOvtNfuAsViZcpL -->

3. create deployment

kubectl create deployment myapp \
  --image=sbeliakou/web-pod-info:v1 \
  --replicas=1

kubectl apply -f myapp-headless.yml

kubectl apply -f myapp-clusterip.yml

kubectl run --rm -it test --image=busybox:1.27 --restart=Never \
nslookup myapp-clusterip

kubectl run --rm -it test --image=busybox:1.27 --restart=Never \
nslookup myapp-headless


<!-- RJqtGrBgf7CA6vLstSTv3zToV -->

4.

kubectl apply -f hello-hello-service.yml 

kubectl get deploy hello-hello -o yaml

The "IP Ghost" Trick (Essential for WSL): Since you're on Minikube, the checker might be trying to hit the Minikube IP (192.168.49.2). Run this to make your WSL machine respond to that IP:

Bash
sudo ip addr add 192.168.49.2/32 dev lo

<!-- KYrz7PfDy0MfaSY9RtFfUOrUP -->