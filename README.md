# Example GitOps-managed Service Mesh

Use this repository as a starting point to manage a Service Mesh on an OpenShift cluster.

## Getting Started

1. Clone this example repository.

2. Configure the example ArgoCD `Application` by providing your new repository URL `spec.source.repoURL` in the following files:

    ```
    bootstrap/instance/application.yaml
    apps/application-service-mesh.yaml
    ```

3. Provision the ArgoCD operator:

    ```
    oc apply -k bootstrap/operator
    ```

4. Provision the ArgoCD `Application`:

    ```
    oc apply -k bootstrap/instance
    ```

## Observation

The demo bootstrap initiates a default ArgoCD instance hosted in the `openshift-gitops` namespace. In this namespace a `Route` is deployed which provides a URL to the ArgoCD console.

## Onboarding an application to the Service Mesh

The following sections will describe how to manage applications deployed to the Service Mesh with this GitOps framework.

### Requesting a new namepaces

New namespaces are added by including their definitions in `servicemesh/overlays/default/namespaces.yaml`. The namespaces `bookinfo-test` and `bookinfo-qa` are commented out there.

### Adding namespaces to a ServiceMeshMemberRoll

If you want new namespaces to be included as a member of the mesh. Add them to `servicemesh/overlays/default/servicemeshmemberroll.yaml`

### Adding ArgoCD Applications (bookinfo example)

You can define applications in the `apps` directory. Example application definitions are available for the sample bookinfo namespaces. Uncomment the lines in `apps/kustomization.yaml` to deploy those apps.

### Validating the bookinfo example
