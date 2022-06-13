# service-policy

```
kubectl run nginx --image nginx:latest 
```

```
kubectl get pod
```

```
kubectl create ns storefront
```

```
kubectl run nginx --image nginx:latest -n storefront
```

```
kubectl expose pod nginx --name nginx-default --type ClusterIP --port 80
```

```
kubectl exec -it nginx -n storefront -- sh 
```

```
curl nginx-default.default.svc
```

```
exit
```

