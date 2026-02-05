1.

Also Create the Headless Service (REQUIRED)

<!-- 9iXlbkOT67fvp4qZJKt4GNngJ -->

2.

<!-- jn3dlTOwU59WtrE8f4aTtmYvL -->

3.

<!-- vRFzAGxhPTMak4ZMYXxQBTwgs -->

4.

kubectl run dns-test \
  --image=busybox:1.34 \
  --restart=Never \
  --rm -it \
  -- sh -c "
nslookup random-generator-0.random-generator.default.svc.cluster.local
nslookup random-generator-1.random-generator.default.svc.cluster.local
nslookup random-generator-2.random-generator.default.svc.cluster.local
" > $HOME/k8s_sts.txt

<!-- Cx30w0WNnruy9teX8f8nrXM8o -->