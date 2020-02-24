There is example of installation [Rancher](https://rancher.com) to [Hetzner Cloud](https://console.hetzner.cloud).
## Rancher installation
1. Create new server with Ubuntu 18.04

2. Update dependencies and install updates
```
sudo apt-get update
sudo apt-get upgrade
```

3. Install docker:
```
sudo apt install docker.io
```

4. Run Docker at start
```
sudo systemctl start docker
sudo systemctl enable docker
```

5. Install Rancher
```
sudo docker run -d --restart=unless-stopped -p 80:80 -p 443:443 rancher/rancher
```

6. Open rancher in browser. Create admin account
```
https://<SERVER_IP>
```

7. Add new cluster
```
1. From the Clusters page, click Add Cluster.
2. Choose Custom.
3. Enter a Cluster Name.
4. Choose "Custom" cloud provider
5. Choose all node roles: etcd, Control Plane, Worker
```

8. Add new nodes: setup new server; install docker; setup Rancher agent by suggested script like this:
```
sudo docker run -d --privileged --restart=unless-stopped --net=host -v /etc/kubernetes:/etc/kubernetes -v /var/run:/var/run rancher/rancher-agent:v2.3.5 --server ...
```
