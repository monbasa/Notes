## Docker GUI(portatiner) Installation in CentOS Linux 7

![](./pics/haha.jpg)

[Portainer](https://www.portainer.io/)

### 1.Step to Step

#### 1.1.CentOS Linux 7.x 

	#yum install -y docker

If you need to access internet by proxy, you need config the following content:

	#mkdir -p /etc/systemd/system/docker.service.d

	#vi /etc/systemd/system/docker.service.d/http-proxy.conf

   		 [Service]
    		Environment="HTTP_PROXY=http://xxx"
    		Environment="HTTPS_PROXY=http://xxx"
    		Environment="NO_PROXY="localhost,127.0.0.1,::1"

#### 1.2.Enable and start docker service.

	#systemctl enable docker --now

### 2.Create Container for portainer

	#docker volume create portainer_data

	#docker run -d -p 8000:8000 -p 9443:9443 -p 9000:9000 --name portainer-ce \
	--restart=always \
	-v /var/run/docker.sock:/var/run/docker.sock \
	-v portainer_data:/data \
	portainer/portainer-ce:2.9.0

### 3.Checking container status, and it is running

	#docker container ls --all

### 4.Access from website as below

	http://local ip:9000
