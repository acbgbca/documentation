# mDNS

mDNS is a local protocol that allows domain resolution using '.local' without needing a local nameserver.

## Setup

mDNS requires the following packages:

```
sudo apt-get install avahi-daemon avahi-utils
sudo systemctl restart avahi-daemon
```

That will setup the mDNS daemon, and start broadcasting <hostname>.local as a DNS resolution.

## Adding domains

Additional domains can be added using the following script:

```
sudo systemctl enable --now avahi-subdomain@<name>.local.service
```

E.g.

```
sudo systemctl enable --now avahi-subdomain@prometheus.local.service
```