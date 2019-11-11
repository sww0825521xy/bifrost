# FIRST STEPS WITH BIFROST {docsify-ignore-all}

## Bifrost System depends on OTA and SSO service, so need to build and deploy OTA and SSO.


### **Build Docker image**
---
#### OTA Build
```bash
sudo docker build -t ota:latest .
```
---
#### SSO Build
```bash
sudo docker build -t sso:latest .
```
---
#### Bifrost Build
```bash
sudo docker build -t bifrost:latest .
```
---




### **Deploy Docker image**
---
#### OTA Deploy
```bash
sudo docker run --name=ota -d -p 8087:8011 ota:latest
```
---
#### SSO Deploy
```bash
sudo docker run --name=sso -d -v /home/weiweishen/deploy/keystore/:/opt/keystore/ -p 8088:8088 sso:latest
```
> [Connected portal](http://cd.android.honeywell.com:8080/H-control_web)
---
#### Bifrost Deploy
```bash
sudo docker run --name=bifrost -d -v /home/weiweishen/deploy/keystore/:/opt/keystore/ -v /home/weiweishen/tools/:/mnt/software/ -v /home/weiweishen/logs/cats/:/usr/local/tomcat/logs/ -p 8080:8080 bifrost:latest
```
> [Bifrost portal](http://cd.android.honeywell.com:8080/cats)
---
#### Nginx Deploy
```bash
sudo docker run -p 80:80 --name my-custom-nginx-container -v /home/weiweishen/tools/logs:/logs -v /home/weiweishen/deploy/nginx/conf/nginx.conf:/etc/nginx/nginx.conf:ro -d nginx
```
---
#### Filebeat Deploy
```bash
sudo docker run -d --name=filebeat --user=root --volume="/home/weiweishen/deploy/beat/filebeat/filebeat.docker.yml:/usr/share/filebeat/filebeat.yml:ro" --volume="/home/weiweishen/tools/logs/monkey:/home/weiweishen/tools/logs/monkey:ro" --volume="/var/run/docker.sock:/var/run/docker.sock:ro" store/elastic/filebeat:7.4.2 filebeat -e -strict.perms=false -E output.elasticsearch.hosts=["172.31.48.76:9200"]
```
---




### **Real time log**
---
#### Bifrost service log
```bash
sudo docker run --restart always --name=catslog -d -p 9001:9001 -v /home/weiweishen/logs/cats:/log mthenw/frontail /log/cats.log
```
> [Bifrost real time log](http://cd.android.honeywell.com:9001/)

---
#### Connected service log
```bash
sudo docker run --restart always --name=connectlog -d -p 9002:9001 -v /home/weiweishen/logs/cats:/log mthenw/frontail /log/hcontrol.log
```
> [Connected real time log](http://cd.android.honeywell.com:9002/)
---
