### Artifactory
#### Pull Docker Image
```bash
docker pull docker.bintray.io/jfrog/artifactory-oss:latest
```
##### Run Docker Image
```bash
docker run --name artifactory-oss -d -v /var/opt/jfrog/artifactory:/var/opt/jfrog/artifactory -p 8081:8081 -e EXTRA_JAVA_OPTIONS='-Xms512m -Xmx2g -Xss256k -XX:+UseG1GC' docker.bintray.io/jfrog/artifactory-oss:latest
```

