# jenkins-docker

## Start

### docker-compose로 구성

```` bash
docker-compose up -d
````

### 직접 구성

https://stackoverflow.com/questions/73110198/jenkins-error-buildind-docker-lib-x86-64-linux-gnu-libc-so-6-version-glibc#comment129133291_73110198

- run jenkins container on detached mode:
```
docker run -u 0 -p 8081:8080 -p 50001:50000 -d -v /var/run/docker.sock:/var/run/docker.sock -v ./jenkins_data/jenkins_home:/var/jenkins_home jenkins/jenkins:lts
```

- Enter the jenkins container as root user:
```
docker exec -it -u0 <container id> bash
```

- Install docker:
```
curl https://get.docker.com > dockerinstall && chmod 777 dockerinstall && ./dockerinstall
```

- And then exit the Jenkins container and change docker.sock privilege to read and write for all users with:

```
sudo chmod 666 /var/run/docker.sock
```
