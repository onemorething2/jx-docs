---
date: 2018-07-20T07:46:49Z
title: "jx upgrade ingress"
slug: jx_upgrade_ingress
url: /commands/jx_upgrade_ingress/
---
## jx upgrade ingress

Upgrades Ingress rules

### Synopsis

Upgrades the Jenkins X Ingress rules

```
jx upgrade ingress [flags]
```

### Examples

```
  # Upgrades the Jenkins X Ingress rules
  jx upgrade ingress
```

### Options

```
      --cluster                  Enable cluster wide Ingress upgrade
  -h, --help                     help for ingress
      --namespaces stringArray   Namespaces to upgrade
      --skip-certmanager         Skips certmanager installation
```

### SEE ALSO

* [jx upgrade](/commands/jx_upgrade/)	 - Upgrades a resource

###### Auto generated by spf13/cobra on 20-Jul-2018