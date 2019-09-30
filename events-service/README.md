Create secrets first

```
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout tls.key -out tls.crt -subj "/CN=svc.artemkv.net"
kubectl create secret tls events-service-tls --key=tls.key --cert=tls.crt
```

Debug the helm chart

```
helm install --debug --dry-run --name dryrun --values values-final.yaml .
```