# Web Application Manifests Source

![Diagram](https://i.postimg.cc/BbhVC1yK/cicd-min.jpg)

This **Multibranch** repository contains the Kubernetes manifests (CD) and is synchronized with 2 Kubernetes custers.

- Code changes are committed to the **[Application Repository](https://github.com/m0dularm1nd/CICD-Api)**, triggering the Jenkins webhook.
- Jenkins first pipeline pulls code from the Git repository, building the application, and pushing the new artifact to the private [Nexus repository](https://nx.v3il.xyz/), then a second pipeline updates new image tags and version.
- ArgoCD manages continuous delivery by syncing with the argo branch to the 1st cluster.
- [FluxCD](https://github.com/m0dularm1nd/FluxCD) source controller syncing flux branch to 2nd cluster.
- Hashi Corp Vault is deployed to seal **Nexus and Postgres DB** credentials secrets using (vault secrets operator).
- Keycloak Provides GUI (Single Sign-On) using OpenID Connect (OIDC) for [Jenkins, Argo, and Grafana](https://v3il.xyz/).
- [**Deployed Web-App live HERE**](https://wall.v3il.xyz/)
