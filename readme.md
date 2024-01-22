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

