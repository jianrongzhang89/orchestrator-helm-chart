
Orchestrator
===========

Helm chart to deploy the Orchestrator solution suite on OpenShift, including Janus IDP backstage, SonataFlow Operator, OpenShift Serverless Operator, Knative Eventing and Knative Serving.



## Configuration

The following table lists the configurable parameters of the Orchestrator chart and their default values.

| Parameter                | Description             | Default        |
| ------------------------ | ----------------------- | -------------- |
| `sonataFlowOperator.isReleaseCandidate` | Indicates RC builds should be used by the chart to install Sonataflow | `false` |
| `sonataFlowOperator.enabled` | whether the operator should be deployed by the chart | `true` |
| `sonataFlowOperator.subscription.namespace` | namespace where the operator should be deployed | `"openshift-serverless-logic"` |
| `sonataFlowOperator.subscription.channel` | channel of an operator package to subscribe to | `"alpha"` |
| `sonataFlowOperator.subscription.installPlanApproval` | whether the update should be installed automatically | `"Automatic"` |
| `sonataFlowOperator.subscription.name` | name of the operator package | `"logic-operator-rhel8"` |
| `sonataFlowOperator.subscription.sourceName` | name of the catalog source | `"redhat-operators"` |
| `sonataFlowOperator.subscription.startingCSV` | The initial version of the operator | `"logic-operator-rhel8.v1.33.0"` |
| `serverlessOperator.enabled` | whether the operator should be deployed by the chart | `true` |
| `serverlessOperator.subscription.namespace` | namespace where the operator should be deployed | `"openshift-serverless"` |
| `serverlessOperator.subscription.channel` | channel of an operator package to subscribe to | `"stable"` |
| `serverlessOperator.subscription.installPlanApproval` | whether the update should be installed automatically | `"Automatic"` |
| `serverlessOperator.subscription.name` | name of the operator package | `"serverless-operator"` |
| `serverlessOperator.subscription.sourceName` | name of the catalog source | `"redhat-operators"` |
| `rhdhOperator.isReleaseCandidate` | Indicates RC builds should be used by the chart to install RHDH | `false` |
| `rhdhOperator.enabled` | whether the operator should be deployed by the chart | `true` |
| `rhdhOperator.enableGuestProvider` | whether to enable guest provider | `false` |
| `rhdhOperator.catalogBranch` | The branch for https://github.com/rhdhorchestrator/workflow-software-templates used to import software templates resources | `"v1.2.x"` |
| `rhdhOperator.secretRef.name` | name of the secret that contains the credentials for the plugin to establish a communication channel with the Kubernetes API, ArgoCD, GitHub servers and SMTP mail server. | `"backstage-backend-auth-secret"` |
| `rhdhOperator.secretRef.backstage.backendSecret` | Key in the secret with name defined in the 'name' field that contains the value of the Backstage backend secret. Defaults to 'BACKEND_SECRET'. It's required. | `"BACKEND_SECRET"` |
| `rhdhOperator.secretRef.github.token` | Key in the secret with name defined in the 'name' field that contains the value of the authentication token as expected by GitHub. Required for importing resource to the catalog, launching software templates and more. Defaults to 'GITHUB_TOKEN', empty for not available. | `"GITHUB_TOKEN"` |
| `rhdhOperator.secretRef.github.clientId` | Key in the secret with name defined in the 'name' field that contains the value of the client ID that you generated on GitHub, for GitHub authentication (requires GitHub App). Defaults to 'GITHUB_CLIENT_ID', empty for not available. | `"GITHUB_CLIENT_ID"` |
| `rhdhOperator.secretRef.github.clientSecret` | Key in the secret with name defined in the 'name' field that contains the value of the client secret tied to the generated client ID. Defaults to 'GITHUB_CLIENT_SECRET', empty for not available. | `"GITHUB_CLIENT_SECRET"` |
| `rhdhOperator.secretRef.k8s.clusterToken` | Key in the secret with name defined in the 'name' field that contains the value of the Kubernetes API bearer token used for authentication. Defaults to 'K8S_CLUSTER_TOKEN', empty for not available. | `"K8S_CLUSTER_TOKEN"` |
| `rhdhOperator.secretRef.k8s.clusterUrl` | Key in the secret with name defined in the 'name' field that contains the value of the API URL of the kubernetes cluster. Defaults to 'K8S_CLUSTER_URL', empty for not available. | `"K8S_CLUSTER_URL"` |
| `rhdhOperator.secretRef.argocd.url` | Key in the secret with name defined in the 'name' field that contains the value of the URL of the ArgoCD API server. Defaults to 'ARGOCD_URL', empty for not available. | `"ARGOCD_URL"` |
| `rhdhOperator.secretRef.argocd.username` | Key in the secret with name defined in the 'name' field that contains the value of the username to login to ArgoCD. Defaults to 'ARGOCD_USERNAME', empty for not available. | `"ARGOCD_USERNAME"` |
| `rhdhOperator.secretRef.argocd.password` | Key in the secret with name  defined in the 'name' field that contains the value of the password to authenticate to ArgoCD. Defaults to 'ARGOCD_PASSWORD', empty for not available. | `"ARGOCD_PASSWORD"` |
| `rhdhOperator.secretRef.notificationsEmail.hostname` | Key in the secret with name defined in the 'name' field that contains the value of the hostname of the SMTP server for the notifications plugin. Defaults to 'NOTIFICATIONS_EMAIL_HOSTNAME', empty for not available. | `"NOTIFICATIONS_EMAIL_HOSTNAME"` |
| `rhdhOperator.secretRef.notificationsEmail.username` | Key in the secret with name defined in the 'name' field that contains the value of the username of the SMTP server for the notifications plugin. Defaults to 'NOTIFICATIONS_EMAIL_USERNAME', empty for not available. | `"NOTIFICATIONS_EMAIL_USERNAME"` |
| `rhdhOperator.secretRef.notificationsEmail.password` | Key in the secret with name defined in the 'name' field that contains the value of the password of the SMTP server for the notifications plugin. Defaults to 'NOTIFICATIONS_EMAIL_PASSWORD', empty for not available. | `"NOTIFICATIONS_EMAIL_PASSWORD"` |
| `rhdhOperator.subscription.namespace` | namespace where the operator should be deployed | `"rhdh-operator"` |
| `rhdhOperator.subscription.channel` | channel of an operator package to subscribe to | `"fast-1.2"` |
| `rhdhOperator.subscription.installPlanApproval` | whether the update should be installed automatically | `"Automatic"` |
| `rhdhOperator.subscription.name` | name of the operator package | `"rhdh"` |
| `rhdhOperator.subscription.source` | name of the catalog source | `"redhat-operators"` |
| `rhdhOperator.subscription.startingCSV` | The initial version of the operator | `""` |
| `rhdhOperator.subscription.targetNamespace` | the target namespace for the backstage CR in which RHDH instance is created | `"rhdh-operator"` |
| `rhdhPlugins.npmRegistry` | NPM registry is defined already in the container, but sometimes the registry need to be modified to use different versions of the plugin, for example: staging(https://npm.stage.registry.redhat.com) or development repositories | `"https://npm.stage.registry.redhat.com"` |
| `rhdhPlugins.scope` |  | `"@redhat"` |
| `rhdhPlugins.orchestrator.package` |  | `"backstage-plugin-orchestrator@1.2.0-rc.1"` |
| `rhdhPlugins.orchestrator.integrity` |  | `"sha512-4C3ZeaGeJdrDWRlWGm1sxiZrfn5cIYynlIsKCcKq+aGpZKJABaKesuvGScBX++jmTbCUMDwPXZmWF20ZzSCuxg=="` |
| `rhdhPlugins.orchestratorBackend.package` |  | `"backstage-plugin-orchestrator-backend-dynamic@1.2.0-rc.1"` |
| `rhdhPlugins.orchestratorBackend.integrity` |  | `"sha512-uF7BVOTQEofTyKGvEW7ipPhbHCjsXw8wvSx1YyAQDSsVgq7l6FckUZN2jT0kXmiGqH2f7C7+xKIAoi/ETn3Kdw=="` |
| `rhdhPlugins.notifications.package` |  | `"plugin-notifications-dynamic@1.2.0-rc.1"` |
| `rhdhPlugins.notifications.integrity` |  | `"sha512-3sKvF+sMzx1dPzSGHlbeePmUTrFKztSRcOQGsP60GHgEfg/g4NHQi2nZMlaYYG4+2/ChMl/CrA0vv481s5bgHg=="` |
| `rhdhPlugins.notificationsBackend.package` |  | `"plugin-notifications-backend-dynamic@1.2.0-rc.1"` |
| `rhdhPlugins.notificationsBackend.integrity` |  | `"sha512-LgW8Jq5a0fxPymQoH99ssvwUz0mZLb3dmUx53LtImdT5+B/cKQ/VKa+iLDe7bMZepwqA0yJmjf/tDwKi8qzNqg=="` |
| `rhdhPlugins.signals.package` |  | `"plugin-signals-dynamic@1.2.0-rc.1"` |
| `rhdhPlugins.signals.integrity` |  | `"sha512-ESZJiXPL5hbE3w0oenBy/iY50V/QS5udqfdY0EggCLz7McsjYuBgz9zyowi87oxt8Sscu/Er9gquqi8gGAo4Dw=="` |
| `rhdhPlugins.signalsBackend.package` |  | `"plugin-signals-backend-dynamic@1.2.0-rc.1"` |
| `rhdhPlugins.signalsBackend.integrity` |  | `"sha512-yFSHfkvq9RTzeWTb+V0mMCxShrbHdad6AhNKZ0wU6ywbjw5N9CaedmD0eG+A7f7XEy3dLsmTxIlYbshdct4TiQ=="` |
| `rhdhPlugins.notificationsEmail.enabled` | whether to install the notifications email plugin. requires setting of hostname and credentials in backstage secret to enable. See value backstage-backend-auth-secret. See plugin configuration at https://github.com/backstage/backstage/blob/master/plugins/notifications-backend-module-email/config.d.ts | `false` |
| `rhdhPlugins.notificationsEmail.package` |  | `"plugin-notifications-backend-module-email-dynamic@1.2.0-rc.1"` |
| `rhdhPlugins.notificationsEmail.integrity` |  | `"sha512-S2+gNOoEyQMPATdfIIB4XvZPLGWqyCiAHsOgfgW3qxjM8paSYoxbhHtGP2m+1BePLSbm9PBjVv54xOWTPyL25A=="` |
| `rhdhPlugins.notificationsEmail.port` | SMTP server port | `587` |
| `rhdhPlugins.notificationsEmail.sender` | the email sender address | `""` |
| `rhdhPlugins.notificationsEmail.replyTo` | reply-to address | `""` |
| `postgres.serviceName` | The name of the Postgres DB service to be used by platform services. Cannot be empty. | `"sonataflow-psql-postgresql"` |
| `postgres.serviceNamespace` | The namespace of the Postgres DB service to be used by platform services. | `"sonataflow-infra"` |
| `postgres.authSecret.name` | name of existing secret to use for PostgreSQL credentials. | `"sonataflow-psql-postgresql"` |
| `postgres.authSecret.userKey` | name of key in existing secret to use for PostgreSQL credentials. | `"postgres-username"` |
| `postgres.authSecret.passwordKey` | name of key in existing secret to use for PostgreSQL credentials. | `"postgres-password"` |
| `postgres.database` | existing database instance used by data index and job service | `"sonataflow"` |
| `orchestrator.namespace` | Namespace where sonataflow's workflows run. The value is captured when running the setup.sh script and stored as a label in the selected namespace. User can override the value by populating this field. Defaults to `sonataflow-infra`. | `"sonataflow-infra"` |
| `orchestrator.sonataflowPlatform.resources.requests.memory` |  | `"64Mi"` |
| `orchestrator.sonataflowPlatform.resources.requests.cpu` |  | `"250m"` |
| `orchestrator.sonataflowPlatform.resources.limits.memory` |  | `"1Gi"` |
| `orchestrator.sonataflowPlatform.resources.limits.cpu` |  | `"500m"` |
| `tekton.enabled` | whether to create the Tekton pipeline resources | `false` |
| `argocd.enabled` | whether to install the ArgoCD plugin and create the orchestrator AppProject | `false` |
| `argocd.namespace` | Defines the namespace where the orchestrator's instance of ArgoCD is deployed. The value is captured when running setup.sh script and stored as a label in the selected namespace. User can override the value by populating this field. Defaults to `orchestrator-gitops` in the setup.sh script. | `""` |



---
_Documentation generated by [Frigate](https://frigate.readthedocs.io)._

