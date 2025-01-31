# dafka-consumer

![Version: 12.0.2](https://img.shields.io/badge/Version-12.0.2-informational?style=flat-square)

A Helm Chart for Dafka Consumer

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| disable | bool | `false` | disable consumer. this remove the deployment and all the pods, useful when you need the consumer group to be inactive (i.e in order to reset offsets) |
| name | string | `nil` | name for this consumer |
| port | int | `3000` | the port to use |
| broker | string | `nil` | the url of the kafka broker |
| replicaCount | int | `1` | pod count |
| image.name | string | `"osskit/dafka-consumer"` | the image name to use |
| image.tag | string | `"12.0"` | the image tag to use |
| logLevel | string | `"WARN"` | Allow to specify log level |
| retryPolicyExponentialBackoff | string | `"50,5000,2"` |  |
| connectionFailureRetryPolicyExponentialBackoff | string | `"5000,300000,2"` |  |
| router | {topic: string, route: string}[] | `nil` | mapping of topics to corresponding routes in target |
| target.baseUrl | string | `nil` | target base url |
| target.port | int | `80` | target port |
| target.useK8sServiceHostName | bool | `true` | use k8s service host name (without going through cluster DNS) |
| target.k8sServiceHostName | string | `nil` | k8s service host name |
| target.healthcheck | string | `nil` | target healthcheck route |
| startupProbe.failureThreshold | int | `10` |  |
| startupProbe.periodSeconds | int | `30` |  |
| livenessProbe.initialDelaySeconds | int | `10` |  |
| livenessProbe.failureThreshold | int | `2` |  |
| livenessProbe.periodSeconds | int | `5` |  |
| resources.requests.cpu | string | `"100m"` | cpu requests |
| resources.requests.memory | string | `"100Mi"` | memory requests |
| resources.limits.memory | string | `"400Mi"` | memory limits |
| podLabels | string | `nil` | labels to add to the pod metadata |
| metrics.enabled | bool | `true` | should prometheus scrape this server |
| metrics.path | string | `"/metrics"` | a path prometheus should scrape metrics from |
| auth.enabled | bool | `false` | should use authentication |
| auth.saslUsername | string | `nil` | sasl username |
| auth.saslMechanism | string | `"PLAIN"` | sasl mechanism (PLAIN or SCRAM-SHA-512) |
| auth.saslPassword | string | `nil` | sasl password (not encrypted) |
| auth.secrets.useOpaqueSecrets | bool | `true` | should mount secrets to opaque secrets |
| auth.secrets.useTrustsore | bool | `false` | should use truststore |
| auth.secrets.gcp.saslPasswordResource | string | `nil` | gcp secret resource for sasl password |
| auth.secrets.gcp.truststoreResource | string | `nil` | gcp secret resource for truststore file |
| auth.secrets.gcp.truststorePasswordResource | string | `nil` | gcp secret resource for truststore password |
| auth.secrets.aws.saslPasswordObjectName | string | `nil` | aws secret object name for sasl password |
| auth.secrets.aws.saslTruststoreObjectName | string | `nil` | aws secret object name for truststore |
| auth.secrets.aws.saslTruststorePasswordObjectName | string | `nil` | aws secret object name for truststore password |
| auth.secrets.vault.saslPasswordSecretPath | string | `nil` | vault secret path for sasl password |
| auth.secrets.vault.saslPasswordSecretKey | string | `nil` | vault secret key for sasl password |
| auth.secrets.vault.truststoreSecretPath | string | `nil` | vault secret path for truststore file |
| auth.secrets.vault.truststoreSecretKey | string | `nil` | vault secret key for truststore file |
| auth.secrets.vault.truststorePasswordSecretPath | string | `nil` | vault secret path for truststore password |
| auth.secrets.vault.truststorePasswordSecretKey | string | `nil` | vault secret key for truststore password |
| kedaScaledObject | object | `{"authenticationRef":{"name":null},"enabled":false,"scaleToZeroOnInvalidOffset":false}` | Keda [ScaledObject](https://keda.sh/docs/2.8/concepts/scaling-deployments/) configuration |
| kedaScaledObject.enabled | bool | `false` | set to enabe scaled object support |
| kedaScaledObject.scaleToZeroOnInvalidOffset | bool | `false` | enables scaling down to zero pods |
| kedaScaledObject.authenticationRef | object | `{"name":null}` | A reference to [TriggerAuthentication](https://keda.sh/docs/2.8/concepts/authentication/) |
| kedaScaledObject.authenticationRef.name | string | `nil` | The name of the TriggerAuthentication |
| podMonitor | object | `{"enabled":false,"labels":{},"sampleLimit":null}` | [PodMonitor](https://github.com/prometheus-operator/prometheus-operator/blob/main/Documentation/api.md#monitoring.coreos.com/v1.podMonitor) configuration |
| podMonitor.enabled | bool | `false` | set to enabe pod monitor support |
| podMonitor.labels | object | `{}` | set labels for the pod monitor |
| podMonitor.sampleLimit | string | `nil` | set sample limit for the pod monitor |
| pdb.enabled | bool | `false` | Set to true to enable |
| jvmOpts | string | `nil` |  |
| prometheusRule.enabled | bool | `false` |  |
| prometheusRule.aivenDefaultRules.enabled | bool | `false` |  |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.11.0](https://github.com/norwoodj/helm-docs/releases/v1.11.0)
