1.

kubectl create deployment nginx-deploy --image=nginx:1.19-alpine --replicas=1

kubectl label deployment nginx-deploy app=nginx-deploy

<!-- pejZXwzzkXPEXvM8MGyTNKh1c -->

2.

kubectl create deployment easy-peasy \
  --image=busybox:1.34 \
  --replicas=5 \
  -- sleep infinity

<!-- bFfC3zcsnDUwVFLIsElU73YdJ -->
3.

kubectl scale deployment nginx-deploy --replicas=6

<!-- 3jSqMKeX0cFY8Rp0GAWj3wwCF -->

4.

<!-- QP2z774hWgNt8ebPCY4POArWl -->

5.

kubectl set image deployment/nginx-deploy nginx=nginx:1.21-alpine

To verify:

kubectl rollout status deployment/nginx-deploy
kubectl describe deploy nginx-deploy | grep Image


<!-- Pl8P2gsj7ake0aHFSeIIeN0ag -->

6. 

kubectl scale deployment lemon -n trouble --replicas=1

<!-- oISUz3YcIMsmzgHtIqiIGDRng -->

7. This is the fix for the task, you just have to edit the deployment orange -n trouble like this.

containers:
- name: orange
  image: alpine
  command:
    - sh
    - -c
    - sleep infinity

<!-- aDKQnublqvWU2lE4AyMj7yXYh -->