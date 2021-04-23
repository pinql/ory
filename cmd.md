---
title: commands
---

## install postgres helm

```bash
helm install postgresql \
    --set postgresqlUsername=postgres \
    --set postgresqlPassword=postgres \
    --namespace dev
    bitnami/postgresql \
```

## install keto

```bash
helm install \
    --set 'keto.config.dsn=postgres://postgres:postgres@172.17.0.5:5432/postgres' \
    keto .
```

## helm chart

secretKeyRef expolained:
<https://kubernetes.io/docs/tasks/inject-data-application/distribute-credentials-secure/#define-container-environment-variables-with-data-from-multiple-secrets>

helm exemple

```yaml
- name: DSN # PRISMA_CONFIG
    valueFrom:
    secretKeyRef:
        name: {{ include "keto.secretname" . }} # prisma-configmap
        key: dsn # PRISMA_CONFIG
```
