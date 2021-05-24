# namespaces

Deploy namespaces with (default) networkpolicies

## Example

```yaml
# Disable all NetworkPolicies
disableNetworkPolicies: false

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

  - name: no-policies
    disableDefaultNetworkPolicies: true
```

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| defaultNetworkPolicies | list | `[]` | NetworkPolicies that will be applied to all namespaces |
| disableNetworkPolicies | bool | `false` | Switch to disable all NetworkPolicies |
| namespaces | list | `[]` | List of namespaces to deploy |

