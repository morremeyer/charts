# postfix-sendonly

Sendonly relay mail services for your cluster

## Setup

You need to provide a valid login for your provider. Currently, only submission on port 465 is supported.

You need to deploy this user credentials into the cluster in a secret, specify its name in `.Values.existingSecret`.

The user name has to be stored in `user`, the password in `password`.

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| affinity | object | `{}` |  |
| autoscaling.enabled | bool | `false` |  |
| autoscaling.maxReplicas | int | `5` |  |
| autoscaling.minReplicas | int | `1` |  |
| autoscaling.targetCPUUtilizationPercentage | int | `80` |  |
| existingSecret | string | `"postfix-sendonly"` |  |
| fullnameOverride | string | `""` |  |
| image.pullPolicy | string | `"IfNotPresent"` |  |
| image.repository | string | `"registry.git.mor.re/docker-images/postfix-sendonly"` |  |
| image.tag | string | `"2022.02.05"` |  |
| imagePullSecrets | list | `[]` |  |
| nameOverride | string | `""` |  |
| nodeSelector | object | `{}` |  |
| podAnnotations | object | `{}` |  |
| podSecurityContext.fsGroup | int | `101` |  |
| relay.host | string | `"smtp.mailbox.org"` |  |
| relay.port | int | `465` |  |
| replicaCount | int | `2` |  |
| resources | object | `{}` |  |
| securityContext | object | `{}` |  |
| service.port | int | `25` |  |
| service.type | string | `"ClusterIP"` |  |
| tolerations | list | `[]` |  |

