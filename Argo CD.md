# Argo CD

ArgoCD and OpenShift are both popular tools in the realm of modern application development and deployment, but they serve different purposes and target slightly different use cases.

**ArgoCD**:

1. **Purpose**: ArgoCD is a declarative, GitOps continuous delivery tool for Kubernetes. It helps in automating the deployment of applications to Kubernetes clusters.
  
2. **Key Features**:
   - Declarative GitOps Workflow: ArgoCD uses Git as a source of truth for declarative infrastructure and application definitions.
   - Continuous Delivery: It continuously monitors application state and updates the target environment to match the desired state defined in Git repositories.
   - Rollback and History: ArgoCD keeps track of application versions and provides an easy way to rollback to previous versions if needed.
   - Multi-Tenancy: Supports multiple users, teams, and environments.
   
3. **Community and Ecosystem**: ArgoCD has a growing community and integrates well with other Kubernetes tools and platforms.

**OpenShift**:

1. **Purpose**: OpenShift is a Kubernetes distribution with additional features and tooling built around it. It's more than just a container orchestration platform; it offers a complete container platform for deploying, managing, and scaling applications.

2. **Key Features**:
   - Kubernetes Distribution: OpenShift is built on top of Kubernetes and provides additional features like developer and operations tooling, built-in monitoring, logging, and security.
   - Developer Experience: OpenShift provides a rich developer experience with features like Source-to-Image (S2I) builds, Developer Console, and CI/CD integration.
   - Operator Framework: OpenShift leverages Kubernetes Operators for managing complex applications and infrastructure.
   - Multi-Tenancy: OpenShift supports multi-tenancy, allowing multiple teams to share the same cluster securely.
   
3. **Community and Ecosystem**: OpenShift has a large community and is backed by Red Hat, which provides enterprise support and a wide range of integrations with other Red Hat products.

**Comparison**:

- **Scope**: ArgoCD focuses primarily on continuous delivery and GitOps workflows for Kubernetes, while OpenShift provides a complete container platform with additional developer and operations tooling.
  
- **Customization**: ArgoCD is highly customizable and can be integrated with various CI/CD tools and workflows. OpenShift, being a complete platform, offers less customization but provides a more comprehensive set of features out of the box.
  
- **Community and Support**: Both have active communities, but OpenShift benefits from the backing of Red Hat, providing enterprise-level support and a wide range of resources for users.

In summary, if your primary focus is on Kubernetes-native continuous delivery and GitOps workflows, ArgoCD might be a better fit. However, if you need a complete container platform with additional developer and operations tooling, OpenShift would be a more suitable choice.

## Videos

 * [Argo CD Synchronization is BROKEN! It Should Switch to Eventual Consistency!](https://www.youtube.com/watch?v=t1Fdse-F9Jw)
	> [<img src="https://img.youtube.com/vi/t1Fdse-F9Jw/0.jpg" width="200">](https://www.youtube.com/watch?v=t1Fdse-F9Jw "Argo CD Synchronization is BROKEN! It Should Switch to Eventual Consistency! by DevOps Toolkit 8,554 views 22 minutes")
 * [How to Apply GitOps on GitHub With Argo CD And Crossplane?](https://www.youtube.com/watch?v=81IJYTWZAfM)
	> [<img src="https://img.youtube.com/vi/81IJYTWZAfM/0.jpg" width="200">](https://www.youtube.com/watch?v=81IJYTWZAfM "How to Apply GitOps on GitHub With Argo CD And Crossplane? by DevOps Toolkit 7,374 views 10 minutes, 13 seconds")
 * [What is ArgoCD](https://www.youtube.com/watch?v=p-kAqxuJNik)
	> [<img src="https://img.youtube.com/vi/p-kAqxuJNik/0.jpg" width="200">](https://www.youtube.com/watch?v=p-kAqxuJNik "What is ArgoCD by IBM Technology 23,257 views 4 minutes, 34 seconds")