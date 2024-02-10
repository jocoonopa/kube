# Helm 啟動教學

## port-forward :8443

```bash

kubectl get pods -n kubernetes-dashboard -l "app.kubernetes.io/name=kubernetes-dashboard,app.kubernetes.io/instance=kubernetes-dashboard" -o jsonpath="{.items[0].metadata.name}"
# kubernetes-dashboard-858f644758-lcnvz
kubectl -n kubernetes-dashboard port-forward kubernetes-dashboard-858f644758-lcnvz 8443:8443

```

## Set TOKEN

```bash
kubectl apply -f https://raw.githubusercontent.com/MikeHsu0618/kubernetes-from-another-world/main/ch4/default-sa.yaml

# print token

TOKEN=$()kubectl -n kube-system describe secret default | awk '$1=="token:"{print $2}')

kubectl config set-credentials docker-desktop --token="${TOKEN}"
```


## TOKEN

eyJhbGciOiJSUzI1NiIsImtpZCI6Ijl0QlJzRlVZWXhtWnJZUkxTZ25ObnlDcFZEVWNvYkNQVVJ6dnlyYUpmb2MifQ.eyJpc3MiOiJrdWJlcm5ldGVzL3NlcnZpY2VhY2NvdW50Iiwia3ViZXJuZXRlcy5pby9zZXJ2aWNlYWNjb3VudC9uYW1lc3BhY2UiOiJrdWJlLXN5c3RlbSIsImt1YmVybmV0ZXMuaW8vc2VydmljZWFjY291bnQvc2VjcmV0Lm5hbWUiOiJkZWZhdWx0Iiwia3ViZXJuZXRlcy5pby9zZXJ2aWNlYWNjb3VudC9zZXJ2aWNlLWFjY291bnQubmFtZSI6ImRlZmF1bHQiLCJrdWJlcm5ldGVzLmlvL3NlcnZpY2VhY2NvdW50L3NlcnZpY2UtYWNjb3VudC51aWQiOiJlMWZhZjA4MS1mODVlLTQ5MmQtODZkYi0xNzA2ZDJhMmNhMGYiLCJzdWIiOiJzeXN0ZW06c2VydmljZWFjY291bnQ6a3ViZS1zeXN0ZW06ZGVmYXVsdCJ9.FJlCQDJ3m0FHLmwx4JBXqAVeQusKdUWsWLLn8WDwgpCGwmIyzSas6w4C27aHQcjIWzmslwqRiJ7wC2CgQtVE3-2dC7QhVIUJX5ot2I-93CPO4nkRbwBU8gNaz85hdVuNnxkmVzT6zO6bSEwp0Ltc-JCic0kr4_BZcLn_4xWRewNhCZZCTqOB2iXyV9xD_4oaTiqYWqljhDy1rIHz5D76FckIhCFkidHI2XrmhWaX4aCoWgmxjChi4RJzgOELfKtbtpienAMtCuCPjK_NbaJvnk5S3BStpy5jf7OrDbC3ajRoB_c9IMqHj3Tw-JLeQqOhUCH1kBKTc1HX9a3B-d-H8w