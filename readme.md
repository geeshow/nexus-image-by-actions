# push nexus image to aws ecr by github actions

## origin image
sonatype/nexus3

## system requirements

## run on local
```bash
docker pull sonatype/nexus3
docker run -d -p 8081:8081 --name nexus sonatype/nexus3
# if your server memory is less than 1G, you should set the memory of nexus to 512m
docker run -d -p 8081:8081 -m 1g --name nexus -e INSTALL4J_ADD_VM_PARAMS="-Xms512m -Xmx512m -XX:MaxDirectMemorySize=512m" sonatype/nexus3
```

### nexus admin password path when the first run
```bash
docker exec -it nexus cat /nexus-data/admin.password
```

### nexus url
http://localhost:8081


sudo yum install -y java-1.8.0
wget https://download.sonatype.com/nexus/3/latest-unix.tar.gz
tar -xvzf latest-unix.tar.gz
wget https://sonatype-download.global.ssl.fastly.net/repository/downloads-prod-group/3/nexus-3.64.0-04-unix.tar.gz
tar -xvzf nexus-3.64.0-04-unix.tar.gz
sudo mkdir /nexus-data
sudo mv nexus-3.64.0-04 /nexus-data/nexus
sudo mv sonatype-work /nexus-data/sonatype-work
sudo useradd nexus
echo 'nexus   ALL=(ALL)       NOPASSWD:ALL' | sudo tee -a /etc/sudoers
sudo chown -R nexus:nexus /nexus-data/nexus
sudo chown -R nexus:nexus /nexus-data/sonatype-work
{ echo ''; echo 'run_as_user="nexus"'; } | sudo tee -a /nexus-data/nexus/bin/nexus.rc
sudo ln -s /nexus-data/nexus/bin/nexus /etc/init.d/nexus
/etc/init.d/nexus start
