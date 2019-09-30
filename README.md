https://docs.bitnami.com/kubernetes/how-to/configure-rbac-in-your-kubernetes-cluster/#use-case-2-enable-helm-in-your-cluster

```
kubectl apply -f tiller-service-account.yaml
```

Run
```
helm init
helm init --service-account tiller --upgrade
```