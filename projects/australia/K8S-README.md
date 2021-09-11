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

## Create the pelias.json ConfigMap
This is the configuration that will be used, I believe it is what makes the setup **project specific** i.e. you need to use the `project/australia/pelias.json` to set up the Australian data.
```
kubectl apply -f shared/shared-pelias-configmap.yaml
```

## Create the shared PVCs
These are for the data and for the blacklist. I'm not sure about the blacklist yet, it appears empty for the Australian project, however it might get filled in later? If it is pre-configured then it will need to become a ConfigMap.
```
kubectl apply -f shared/shared-data-claim-persistentvolumeclaim.yaml
kubectl apply -f shared/shared-blacklist-claim-persistentvolumeclaim.yaml
```

## Run the download job/s
This will spin up all of the download jobs in parallel and download files to the data PVC.

```
kubectl apply -f shared/shared-download-all-job.yaml
```