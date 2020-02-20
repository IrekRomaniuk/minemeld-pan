[Running MineMeld Using Docker](https://live.paloaltonetworks.com/t5/MineMeld-Articles/Running-MineMeld-using-Docker/ta-p/289062)

![Minemeld](https://github.com/IrekRomaniuk/minemeld-pan/raw/master/Minemeld.jpg)

### Install & Run MineMeld
##### Pull the latest official image
```
sudo docker pull paloaltonetworks/minemeld
```
##### Create named volumes for data and logs
```
sudo docker volume create minemeld-logs
sudo docker volume create minemeld-local
```
##### Start the container
```
sudo docker run -dit --name minemeld --restart unless-stopped --tmpfs /run -v minemeld-local:/opt/minemeld/local -v minemeld-logs:/opt/minemeld/log  -p 443:443 -p 80:80 paloaltonetworks/minemeld
```

### Kuberenets

```
$kubectl apply -f minemeld.yaml
deployment.extensions/mm-pa created
service/mm-pa created

$ kubectl get pods | grep mm
mm-pa-859c7b4fc9-hfgd5               1/1     Running   0          12m
$ kubectl get svc | grep mm
mm-pa                         LoadBalancer   192.168.172.117   10.44.1.44      443:31437/TCP    12m

```

