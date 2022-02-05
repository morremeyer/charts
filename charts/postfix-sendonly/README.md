# postfix-sendonly

Sendonly mail services for your cluster

## Creating a DKIM key

To create the needed DKIM key, follow the instructions in [„Generating a DKIM key“](https://git.mor.re/docker-images/postfix-sendonly#generating-a-dkim-key).

You need to deploy this key into the cluster in a secret, specify its name in `.Values.existingSecret`.
The DKIM private key has to be stored in the key `key`.

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| affinity | object | `{}` |  |
| autoscaling.enabled | bool | `false` |  |
| autoscaling.maxReplicas | int | `5` |  |
| autoscaling.minReplicas | int | `1` |  |
| autoscaling.targetCPUUtilizationPercentage | int | `80` |  |
| domain | string | `nil` |  |
| existingSecret | string | `"postfix-sendonly-dkim"` |  |
| fullnameOverride | string | `""` |  |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.repository | string | `"registry.git.mor.re/docker-images/postfix-sendonly"` |  |
| image.tag | string | `"2022.02.05"` |  |
| imagePullSecrets | list | `[]` |  |
| nameOverride | string | `""` |  |
| nodeSelector | object | `{}` |  |
| podAnnotations | object | `{}` |  |
| podSecurityContext | object | `{}` |  |
| replicaCount | int | `2` |  |
| resources | object | `{}` |  |
| securityContext | object | `{}` |  |
| service.port | int | `25` |  |
| service.type | string | `"ClusterIP"` |  |
| tolerations | list | `[]` |  |

