# Setup

This is all relative to the `k8s/` directory in projects/australia.

## Deploy elasticsearch
```
kubectl apply -f elasticsearch
```

## Run the schema job
```
kubectl apply -f schema/schema-job.yaml
```

