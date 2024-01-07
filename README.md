# GITOPS

### what is GitOps?
GitOps can be consider an extention of Infrastructure of Code (IAC) that uses Git as the version control system.

### GitOps Principals
- GitOps is declarative
- GitOps apps are Versioned and Immutable
- GitOps apps pulled automatically
- GitOps apps are continuously Reconsile.

### GitOps vs DevOps
- Gitops is typically used in containerization technologies like openshift and kubernets
- DevOps can be used with any applications
- In DevOps pipeline the changes were pushed to the cluster
- In GitOps changes were pulled by the operator.

### Pushed vs Pull Based Deployment

#### Pushed Based Approach
- In Push based approach the application code goes through various stages of a CI-CD pipeline and the updates pushed to the kubernetes cluster.
- To pushing the updates CI system has read-write access to the kubernetes cluster for those we need to expose the credentials outside the cluster and store them in a CI system. This raises potential issues and not recommended.
- Apart from this CI system has readyonly access to the GIT repository and read-write access to the container. Whereas the k8 cluster has ready only access to the container registry.

#### Benefits
- Deploying helm charts can be done easier.
- Container versions updates can be injected by build pipeline.
- Secrets management is easier.

#### Challenges
- Cluster config are embedded inside the CI system
- CI system has Read-Write access to the cluster
- Deployment approach coupled to the CD system.

#### Pull Based Approach 
- GitOps operator deploy new images from running inside kubernets cluster.
- Operator can check either container repository where new images or git repository for manifest updates
- In Pull Based approach CI system has read-write access to the container registry and it does not access to the kubernets cluster.

#### Benefits
- No external user/client has the right to modify the clusters
- Scan container registry for new versions/
- Secrets in Git repository via HashiCorp Vault
- Deployment approach is not coupled to CD pipeline.
- GitOps operator supports multi-tenant model.

#### Challenges
- Managing Secrets of Helm charts deployment is harder
- Generic Secrets management ic complex. 


### GitOps Benefits and Challenges

- Lightweight and Vendor-neutral
- Faster, Safer, Immutable and Reproducible Deployment
- Eliminating configuration Drift
- Uses familiar tools and processes
- Revisions with history.

- Desn't helm with secret management
- Number of Git Repositories 
- Challenges with programmatic updates
- Governance other than PR approval
- Malformed YAML/Config manifest