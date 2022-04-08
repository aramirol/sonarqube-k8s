# sonarqube-k8s

[![git-sync](https://github.com/aramirol/sonarqube-k8s/actions/workflows/git-sync.yml/badge.svg)](https://github.com/aramirol/sonarqube-k8s/actions/workflows/git-sync.yml)

## What is?

[![Kubernetes](https://img.shields.io/badge/kubernetes-v1.19.x-blue?logo=kubernetes&logoColor=lightgrey)](https://github.com/aramirol/istio-example)
[![Kubernetes](https://img.shields.io/badge/sonarqube-lts_community-blue?logo=sonarqube&logoColor=lightgrey)](https://github.com/aramirol/istio-example)
[![License](https://img.shields.io/badge/license-MIT-green?logo=github&logoColor=lightgrey)](https://github.com/aramirol/sonarqube-k8s/blob/main/LICENSE.md)

This is a tutorial about how to deploy Sonarqube on a Kubernetes Cluster easily.

## Requirements

As we use **hostPath PVs** you must have created the needed directories before the deploy.

```sh
$ mkdir /data/sonarkube_k8s/sonarqube-postgres/
$ chmod 777 /data/sonarkube_k8s/sonarqube-postgres
```
```sh
$ mkdir /data/sonarkube_k8s/sonarqube-data/
$ chmod 777 /data/sonarkube_k8s/sonarqube-data
```

## How to
### Manual deploy

You need to download the repository files: 

```sh
$ git clone https://github.com/aramirol/sonarqube-k8s.git
```

Then, launch the following command to deploy SonarQube on Kubernetes:

```sh
$ kubectl apply -f ./sonarqube-k8s/kubernetes/deploy_sonarqube_k8s.yml
    "namespace/sonarqube" created
    "persistentvolume/sonarqube-postgres-pv" created
    "persistentvolumeclaim/sonarqube-postgres-pvc" created
    "configmap/postgres" created
    "service/postgres" created
    "deployment.apps/postgres" created
    "persistentvolume/sonarqube-data-pv" created
    "persistentvolumeclaim/sonarqube-data-pvc" created
    "configmap/sonarqube-config" created
    "service/sonarqube" created
    "deployment.apps/sonarqube" created
    "ingress.networking.k8s.io/ingress-sonarqube" created
```

**NOTE:** It may take a few minutes for the app to be up and running.

## Delete App

You can use the same deploy yaml file to delete all objects. Just use the following command:

```sh
kubectl delete -f ./sonarqube-k8s/kubernetes/deploy_sonarqube_k8s.yml
    namespace "sonarqube" deleted
    persistentvolume "sonarqube-postgres-pv" deleted
    persistentvolumeclaim "sonarqube-postgres-pvc" deleted
    configmap "postgres" deleted
    service "postgres" deleted
    deployment.apps "postgres" deleted
    persistentvolume "sonarqube-data-pv" deleted
    persistentvolumeclaim "sonarqube-data-pvc" deleted
    configmap "sonarqube-config" deleted
    service "sonarqube" deleted
    deployment.apps "sonarqube" deleted
    ingress.networking.k8s.io "ingress-sonarqube" deleted
```

## License

MIT License

See [LICENSE](https://github.com/aramirol/sonarqube-k8s/blob/main/LICENSE) to see the full text.
