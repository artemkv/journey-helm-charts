Create secrets first

```
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout tls.key -out tls.crt -subj "/CN=svc.artemkv.net"
kubectl create secret tls events-service-tls --key=tls.key --cert=tls.crt
```

Debug the helm chart

```
helm install --debug --dry-run --name dryrun --values values-final.yaml .
```

Install helm chart
```
helm install --name barcelona --values values-final.yaml --set=image.tag=<TAG> .
```

Update helm chart
```
helm upgrade --recreate-pods barcelona --values values-final.yaml --set=image.tag=<TAG> .
```

Rollback to previous release
```
helm rollback barcelona 0
```

Delete helm chart
```
helm delete --purge barcelona
```