# Tekton Build Pipeline

## Prepare Tekton

You need to install Tekton once into the cluster. See the installation documentation how to do that: https://github.com/tektoncd/pipeline/blob/master/docs/install.md

## Prepare the namespace

To separate your work from the rest of the cluster, create a workspace by applying the `pipeline/namespace.yaml` file.

```
$ kubectl apply -f pipeline/namespace.yaml
```

## Prepare Docker secrets

In order to use DockerHub you need to add a secret to the cluster:

```
kubectl create secret docker-registry regcred --docker-username=<your-user-name>  --docker-password="<your-password>" --docker-email="<your-mail-address>"
```

## Run the pipeline

Now you can run the task via:

```
$ kubectl apply -f pipeline
$ tkn taskrun describe build-docker-image-from-git-source-task-run
$ tkn taskrun logs build-docker-image-from-git-source-task-run -f
```