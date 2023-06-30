
A little POC of for calculating and remediating flux

kind create cluster --config kind.yaml && kind export kubeconfig --internal && tilt ci

access goldilocks
kubectl port-forward -n goldilocks service/goldilocks-dashboard 8080:80

access-grafana:
kubectl -n monitoring port-forward svc/kube-prometheus-stack-grafana 3000:80
http://localhost:3000/d/flux-control-plane/flux-control-plane?orgId=1&refresh=10s

```
username: admin
password: prom-operator
```

 kube-burner init --config config.yaml