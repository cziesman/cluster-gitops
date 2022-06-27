# Example GitOps-managed Service Mesh

Use this repository as a starting point to manage a Service Mesh on an OpenShift cluster.

## Installation

Provision the ArgoCD operator:

```
oc apply -k bootstrap/operator
```

Provision the ArgoCD `Application`:

```
oc apply -k bootstrap/instance
```

## Observation

The demo bootstrap initiates a default ArgoCD instance hosted in the `openshift-gitops` namespace. In this namespace a `Route` is deployed which provides a URL to the ArgoCD console.
