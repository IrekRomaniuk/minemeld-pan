[Running MineMeld Using Docker](https://live.paloaltonetworks.com/t5/MineMeld-Articles/Running-MineMeld-using-Docker/ta-p/289062)

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
