## Getting started

```
docker-compose build
```

Several ways to proceed from here.
You can use
```
docker-compose up -d
```

## Get initial password
```
docker exec -it jenkins_test cat /var/jenkins_home/secrets/initialAdminPassword
```

## Start slave container
Open master
```
docker-compose run -d slave -url http://192.168.99.100:8080 06647f7ff6fa31688663191eb7e62347c4b76b5a4f9a59c11a2edb3ad2e35899 slave1
```
where ``06647f7ff6fa31688663191eb7e62347c4b76b5a4f9a59c11a2edb3ad2e35899`` is secret and slave name ``slave1`` you get from master jenkins when you create slave node.


## Backup data from volume

To backup the data from the volume container is simple to. Simply run:

```
docker cp jenkins-dv:/var/jenkins_home /tmp/jenkins-backup
```

## Performance


Java 1.8
```
docker run -p 8080:8080 --name=jenkins-master -d --env JAVA_OPTS="-Xmx8192m" jenkins
```
Java 1.7
```
docker run -p 8080:8080 --name=jenkins-master -d --env JAVA_OPTS=”-Xmx8192m -XX:PermSize=256m -XX:MaxPermSize=1024m” jenkins
```

## Link
[Official Jenkins master image](https://hub.docker.com/_/jenkins/)
[Official Jenkins image repo](https://github.com/jenkinsci/docker)
[Jenkins setup example 1](https://github.com/kaeff/jenkins-phoenix)
[Putting Jenkins in a Docker Container](https://engineering.riotgames.com/news/putting-jenkins-docker-container)
[Cloudbees Jenkins slave image](https://github.com/cloudbees/jnlp-slave-with-java-build-tools-dockerfile)

## Slave on demand
[Stackoverflow](http://stackoverflow.com/questions/38616906/jenkins-trigger-on-demand-slaves-in-dockers?rq=1)
[Docker Swarm and slaves in containers](http://paweloczadly.github.io/devops/2014/12/17/jenkins-slave-as-docker-container)
