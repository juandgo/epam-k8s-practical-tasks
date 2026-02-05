
2. 

kubectl get pods --all-namespaces | grep save-me

kubectl get pod save-me -n find-me -o yaml > $HOME/k8s_pods/save-me-pod.yml

<!-- rb1YuGbPlOVQz5i11FyQAAghS -->

3.

kubectl describe pod web -n trouble

kubectl set image pod/web web=nginx:1.19-alpine -n trouble

<!-- jPESjAjiXhWqtzTU4Sj12RcoA -->

4.
kubectl edit pod redis-db -n trouble
kubectl delete pod redis-db -n trouble

cat <<EOF | kubectl apply -f -
apiVersion: v1
kind: Pod
metadata:
  name: redis-db
  namespace: trouble
  labels:
    name: redis-db
spec:
  containers:
  - name: redis-db
    image: busybox
    command: ["sh", "-c"]
    args: ["sleep infinity"]
EOF

<!-- 55nfmjvuU6hpk8w9wHWHXjnKV -->

7.

# Ensure the directory exists
mkdir -p $HOME/k8s_pods

# Save the logs to the log file
kubectl logs envtest > $HOME/k8s_pods/default-envtest.log

# Verify the content (Optional)
cat $HOME/k8s_pods/default-envtest.log

<!-- NBauHogyOkKA3zdzKezQ7YPP1 -->

9.
k delete pods -n clean-up --all 

<!-- FkdDHi8ARev3DdAq770KwEv2g -->

10.

# Create the namespace if you haven't
kubectl create ns static 

# Copy the file to the magic directory
sudo cp 10-static-pod.yml /etc/kubernetes/manifests/

--- Using minikube

minikube ssh

sudo sh -c 'cat <<EOF > /etc/kubernetes/manifests/nginx-static.yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx-static
  namespace: static
  labels:
    app: nginx-static
spec:
  containers:
  - name: nginx
    image: nginx:alpine
    ports:
    - containerPort: 80
EOF'

exit

<!-- D9y8LnwPurcs5kihQFV3Pqaw8 -->

11.

minikube ssh "sudo rm /etc/kubernetes/manifests/nginx-static.yaml"
<!-- EAPPDfNwV7lPWPKlBdj21zKVZ -->