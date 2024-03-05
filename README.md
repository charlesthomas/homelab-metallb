# homelab-metallb

This is a mirco-services repo for deploying
[metallb](https://metallb.org)
into [my homelab](https://github.com/charlesthomas/homelab).

## pools

### internal

192.168.1.40 - 192.168.1.99

external to the k3s cluster, but internal to the network.
ie not exposed to the internet

```yaml
annotations:
  metallb.universe.tf/address-pool: internal
```

### external

192.168.1.5/32

for port forwarding from the router,
once i have services i want to be able to access from the open internet

```yaml
annotations:
  metallb.universe.tf/address-pool: external
```

### dns

192.168.1.8/32

i probably could have done this with a different annotation,
and maybe without a pool at all,
but i wanted to make sure .8 was always accessible for [pihole](/pihole/)


```yaml
annotations:
  metallb.universe.tf/address-pool: dns
```

---
This repo is templated via
[homelab-template](https://github.com/charlesthomas/homelab-template)
and automatically updated via
[🤖 Templatron](https://github.com/charlesthomas/templatron).
