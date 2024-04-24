# Creating Business Cluster using Argocd
## Deployment of crossplane components
1. In order for the business cluster to be up and running, the following crossplane components should be deployed
   - Controller-config
   - Provider
   - Provider-config
   - Composite Resource Definition
   - Composition
   - Clusterclaim
2. Of the above components, auto-sync for provider-config and composite resource definition will be disabled. This is done so that they can wait for provider to arrive at healthy state.
3. The clusterclaim file will point to a empty directory (infra/clusters/cluster-configs) and when the cluster is required the clusterclaim yaml is to be added in the mentioned directory and argocd will automatically sync and deploy clusterclaim thereby triggering cluster creation.

## Deployment of business cluster apps
1. The default apps to be deployed in business cluster is also synced via argocd under 'clusters' application. It is set to auto-sync by default.
2. Customer specific apps can be added under the same application and will be automatically deployed 
