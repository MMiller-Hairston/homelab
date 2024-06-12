# Homelab

This repo is to configure an Ubuntu Server running on [Mini PC](https://www.amazon.com/dp/B0BYJDFG5B?psc=1&ref=ppx_yo2ov_dt_b_product_details). These instructions should theoretically still apply to any machine or VPS as long as it is running Ubuntu Server. This repo will serve as documentation so I can remember the setup and reproduce it when needed.

1. Install MicroK8s

```bash
sudo snap install microk8s --classic
```

2. Enable firewall to allow pod<->pod and pod<->internet communication

```bash
sudo ufw allow in on cni0 && sudo ufw allow out on cni0
sudo ufw default allow routed
```

3. Enable core plugins.

```bash
microk8s enable dns
microk8s enable hostpath-storage
microk8s enable helm
```

After this point, everything else in the cluster will be managed with helm charts.
