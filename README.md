# Tekton Build Pipeline

## Docker Hub

To use Docker Hub you need to add a secret to the cluster:

```
kubectl create secret docker-registry regcred --docker-username=<your-user-name>  --docker-password="<your-password>" --docker-email="<your-mail-address>"
```

Now you can run the task via:
```
kubectl apply -f 01_prepare
kubectl apply -f 02_pipeline
kubectl get tekton-pipelines
tkn taskrun describe build-docker-image-from-git-source-task-run
```