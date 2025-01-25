# Manifests Source

![Diagram](https://i.postimg.cc/BbhVC1yK/cicd-min.jpg)

This Multibranch repository holds the Kubernetes manifests and is synchronized with 2 selfhosted Kubernetes RKE2 clusters, as an example(production/staging)

- Code changes are committed to the **[Application Git repository](https://github.com/m0dularm1nd/CICD-Api)**, triggering the next steps via a webhook.
- Jenkins first pipeline pulls code from the Git repository, building the application, and pushing the new artifact to the private Nexus repository, then a second pipeline updates new image tags and version.
- ArgoCD manages continuous delivery by syncing with the argo branch to the 1st cluster.
- [FluxCD](https://github.com/m0dularm1nd/FluxCD) source controller syncing flux branch to 2nd cluster.
- Hashi Corp Vault is deployed to seal Nexus credentials secrets using (vault secrets operator).
- Keycloak Provides GUI (Single Sign-On) using OpenID Connect (OIDC) for jenkins, argo, and grafana.
