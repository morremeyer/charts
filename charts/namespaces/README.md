# namespaces

![Version: 2.0.1](https://img.shields.io/badge/Version-2.0.1-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square)

Deploy namespaces with (default) networkpolicies

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| morremeyer | charts@mor.re |  |
| ekeih |  |  |

## Example

```yaml
# Disable all NetworkPolicies
disableNetworkPolicies: false

defaultNetworkPolicies:
  # Deny all egress traffic
  default-policy:
    spec:
      podSelector:
        matchLabels:
          role: db
      policyTypes:
        - Egress

namespaces:
  test:
    labels:
      meta.mor.re/testlabel: hallo
    networkPolicies:
      testpolicy:
        spec:
          podSelector:
            matchLabels:
              role: db

  no-policies:
    disableDefaultNetworkPolicies: true
```

## Upgrading

### To 2.0.0

The format to define namespaces and network policies has changed. Previously both were specified as a `list` with a `name` key. With this release a `map` is used instead with the name as key. This makes it possible to split the values into several files and merge them with helm.

Old:

```yaml
defaultNetworkPolicies:
  # Deny all egress traffic
  - name: default-policy
    spec:
      podSelector:
        matchLabels:
          role: db
      policyTypes:
        - Egress

namespaces:
  - name: test
    labels:
      meta.mor.re/testlabel: hallo
    networkPolicies:
      - name: testpolicy
        spec:
          podSelector:
            matchLabels:
              role: db
```

New:

```yaml
defaultNetworkPolicies:
  # Deny all egress traffic
  default-policy:
    spec:
      podSelector:
        matchLabels:
          role: db
      policyTypes:
        - Egress

namespaces:
  test:
    labels:
      meta.mor.re/testlabel: hallo
    networkPolicies:
      testpolicy:
        spec:
          podSelector:
            matchLabels:
              role: db
```

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| defaultNetworkPolicies | object | `{}` | NetworkPolicies that will be applied to all namespaces |
| disableNetworkPolicies | bool | `false` | Switch to disable all NetworkPolicies |
| namespaces | object | `{}` | List of namespaces to deploy |
