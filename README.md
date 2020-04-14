# Kuberenetes Postgres Deployment

This repo represents learning about Kubernetes is deploying Postgresql to a kuberenetes development cluster with minikube. This tutorial was written
to ovrecome the fact that kubernetes offical documentation use mysql as it's example and not postgres.

## Prerequistes

[Install Minikube](https://kubernetes.io/docs/tasks/tools/install-minikube/)

### Note on Fedora 31 & 32:

Fedora, like most other Redhat sponsored products, is moving over to using podman. While podman is now supported by minikube, in Fedora 31+
there is systemd bug that prevents podman to being used during installation. In this case, when starting minikube the first time `minikube start`,
the virtual machine environment should be specified as KVM2 (and KVM but be installed). This can be done by start minikube with:

```
minikube start  --drvier=kvm2
```

## Single Instance deployment

To start with a simple example, it is easiest to first try a single instance for a stateful application in kuberenetes.

to test with psql afte deployment:

```
kubectl run -it --rm --image=postgres:12 --restart=Never psql-client -- psql -p 5432  "postgresql://postgres:400dexter@postgresql/postgres"
```
