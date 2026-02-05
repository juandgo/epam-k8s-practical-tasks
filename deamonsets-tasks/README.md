1. Create a new node and set up worker role for it:

minikube node add

kubectl get nodes

kubectl label node minikube-m02 node-role.kubernetes.io/worker=

kubectl get nodes --show-labels

<!-- KrMDaBt6HinRKAzjIaWcBZqnO -->

2. Taint your nodes:

kubectl taint node minikube \
node-role.kubernetes.io/control-plane=:NoSchedule

kubectl taint node minikube-m02 \
node-role.kubernetes.io/worker=:NoSchedule

<!-- m0miKNbBfg9r5VRoVCvxhbnWr -->

3. execute fluent-ds.yml file

<!-- q29eNUK4J92ke3dj4UH6z92eZ -->

4.

kubectl edit ds fluentd-elasticsearch

Add tolerations:

    spec:
      tolerations:
        - operator: "Exists"

<!-- m0miKNbBfg9r5VRoVCvxhbnWr -->

5.

minikube node add

kubectl get nodes

kubectl label node minikube-m03 node-role.kubernetes.io/worker=

kubectl taint node minikube-m03 \
node-role.kubernetes.io/worker=:NoSchedule

6.

sudo apt install -y jq

kubectl get nodes -o json | jq '.' > $HOME/nodes-info.json

7.

<!-- ejYZylCnKjoseXtTe5auIyWPJ -->