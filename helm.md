# Helm Notes

- 12 Factor app
- Helm can define the service and dependencies it works with
- Better application portability and rollbacks
- Faster dev-onboarding
- Helm can let you specify the order of dependencies
- Helm lets you deploy microservice architectures
- You can have a chart for nginx, sql, node, etc
- Chart repository: Dockerhub for charts
- Release: Chart that is deployed
- Helm tracks all of your releases for rollbacks and comparisons

### Helm Components
- Client: helm client
- Client: templating engine
- Tiller: Lives in Cluster, manages releases, history and introspection
- Tiller runs as a service inside of a K8's cluster when you initialize helm
- When you create a chart, you create a package of what
- Template and values file. 
- You can have different values files for different environments

### Benefits of Helm
- Test a chart, deploy it into Artifactory where my users can self serve it to test it themselves. You could use that for product feedback. Demos of your software for your Sales team. 
- Take a change to a service or a set of services. You dont need a staging server, you can spin up a namespace, spin up testing, and have confidence that it will be recreated in the same exact way.







- Codefresh, Xray
