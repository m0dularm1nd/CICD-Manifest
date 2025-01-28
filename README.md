# Web Application Manifests Source

![Diagram](https://i.postimg.cc/BbhVC1yK/cicd-min.jpg)

This **Multibranch** repository contains the Kubernetes manifests (CD) and is synchronized with 2 [Kubernetes custers](https://lamp.v3il.xyz/) with ingress-controller and external access to cluster, providing routing and SSL termination.

- Code changes are committed to the **[Application Repository](https://github.com/m0dularm1nd/CICD-Api)**, triggering the Jenkins webhook.
- [Jenkins](https://jen.v3il.xyz/) first pipeline pulls code from the Git repository, building the application, and pushing the new artifact to the private [Nexus repository](https://nx.v3il.xyz/), then a second pipeline updates new image tags and version.
- [ArgoCD](https://argo.v3il.xyz/) controller by syncing with the argo branch to the 1st cluster.
- [FluxCD](https://github.com/m0dularm1nd/FluxCD) controller syncing flux branch to 2nd cluster.
- [HC Vault](https://vault.v3il.xyz/) is deployed to seal **Nexus and Postgres DB** credentials secrets using (vault secrets operator).
- [Keycloak](https://key.v3il.xyz/) Provides GUI (Single Sign-On) using OpenID Connect (OIDC) for [Apps](https://v3il.xyz/).
- [Prometheus](https://g.v3il.xyz/) operator, Grafana and Loki for monitoring and logging of applications and Kubernetes cluster-wide metrics.

[**Deployed Web-App live HERE**](https://wall.v3il.xyz/)
