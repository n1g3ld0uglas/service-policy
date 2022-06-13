# service-policy

Create an nginx pod in the ```default``` network namespace:
```
kubectl run nginx --image nginx:latest 
```

Confirm the pod was created in the ```default``` namespace:
```
kubectl get pod
```

Create the namespace ```storefront```:
```
kubectl create ns storefront
```

Create an nginx pod in the ```storefront``` namespace:
```
kubectl run nginx --image nginx:latest -n storefront
```

Expose the ```default``` namespace pod as service of type ```ClusterIP```:
```
kubectl expose pod nginx --name nginx-default --type ClusterIP --port 80
```

Exec into the nginx pod within the namespace ```storefront```:
```
kubectl exec -it nginx -n storefront -- sh 
```

Confirm the connevct to the nginx service in the default namespace is ```accepted```:
```
curl nginx-default.default.svc
```

```
exit
```

It works!

<br/>
<br/>


Apply a network policy to break the connection:
```
kubectl apply -f https://raw.githubusercontent.com/n1g3ld0uglas/service-policy/main/service-policy.yaml
```

Again, exec into the nginx pod in the ```storefront``` namespace:
```
kubectl exec -it nginx -n storefront -- sh
```

This time see if the connection is accepted:
```
curl nginx-default.default.svc
```

It fails!

<br/>
<br/>
