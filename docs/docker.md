---
sort: 1
text: |
  ABCDEFGHIJKLMNOPQRSTUVWXYZ
  abcdefghijklmnopqrstuvwxyz
  1234567890
  $B0lFs;0;M8^O;<7H,6e==I4@ih_>eCf2<:81&Bg>.=U2F=)E_ElFn@>KL6bLZ?e2PEZ(B
---


{:.font-body}

# container
## Jenkins

Act/Stb$B9=@.$N(B



$B%^%9%?!<(B/$B%9%l!<%V9=@.$N(BJenkins$B$r%m!<%+%k4D6-$K(Bdocker-compose$B$G9=C[$9$k(B

[docker-compose$B$G$N(BJenkins$B9=C[(B](https://qiita.com/KWS_0901/items/34d09b472bea9f5227a7)

[Jenkins $B:G?7>pJs(B](https://hub.docker.com/_/jenkins?tab=tags&page=1&ordering=last_updated)

### $B%^%9%?!<%3%s%F%J$N:n@.(B
docker-compose.yml$B%U%!%$%k$rMQ0U$9$k(B

`~/docker/docker-jenkins$ vi docker-compose.yml`

jenkins_home$B%G%#%l%/%H%j$N:n@.$H8"8BJQ99(B

`~/docker/docker-jenkins$ mkdir jenkins_home`

`~/docker/docker-jenkins$ sudo chown -R 1000:1000 jenkins_home`

$B%^%9%?!<%3%s%F%J$N5/F0(B

`~/docker/docker-jenkins$ docker-compose up -d`

$B%3%s%F%J(BID$B$r3NG'$7!"%^%9%?!<%3%s%F%J$KF~$k(B

`$ sudo docker ps`

`$ sudo docker exec -it <$B%3%s%F%J(BID> /bin/bash`

$B4IM}<T%Q%9%o!<%I$r<hF@(B

`$ cat /var/jenkins_home/secrets/initialAdminPassword`

\*\*\*\*\*\*\*\*\*\*
<!-- 45550eb526dc4682a5529a7d2488ccff -->

jenkins_home/.ssh/$B$K(BSSH$BG'>Z%-!<$r:n@.$9$k(B

`$ ssh-keygen -t rsa -C ""`

$B%^%9%?!<%3%s%F%J$rDd;_$9$k(B

`(jenkins$B$N(Bdocker$BFb(B)$ exit`

`$ sudo docker-compose stop`

### $B%9%l!<%V%3%s%F%J$N:n@.(B

$B%9%l!<%V%3%s%F%JMQ$N(BDockerFile$B$r:n@.$7!"(Bdocker-compose.yml$B$HF10l$N%U%)%k%@$K3JG<$9$k(B

`~/docker/docker-jenkins$ vi DockerFile_SLAVE`

docker-compose.yml$B$K%9%l!<%V%3%s%F%JMQ$N%5!<%S%9@_Dj$rDI2C$9$k(B

`~/docker/docker-jenkins$ vi docker-compose.yml`

$B%3%s%F%J$r5/F0(B

`~/docker/docker-jenkins$ sudo docker-compose up -d`

## knowledge
$B<+J,$N%J%l%C%8%Y!<%9MQ$K(Bknowledge$B%3%s%F%J$r(BDockerFile/docker-compose$B$rMQ$$$F5/F0$9$k(B

[knowledge$B$N9=C[(B](https://syachiku.net/knowledge-install/)

[docker-knowledge$B$N(BDockerFile Github](https://github.com/support-project/docker-knowledge)

DockerFile$B$N%@%&%s%m!<%I(B

`~$ cd ~/docker/`

`~/docker$ git clone https://github.com/support-project/docker-knowledge.git`

docker-compose.yml$B$r<+4D6-8~$1$K%+%9%?%^%$%:(B

`~/docker/docker-knowledge$ vi docker-compose.yml`

&nbsp;&nbsp;&nbsp; PORT 8080:8080

&nbsp;&nbsp;&nbsp; POSTGRES_PASSWORD=\*\*\*\*\*

cocker-compose$B$+$i9=C[$9$k(B

`~/docker/docker-knowledge$ sudo docker-compose up -d`

&nbsp;&nbsp;&nbsp; up : $B:n@.$H3+;O(B

&nbsp;&nbsp;&nbsp; -d : $B%G!<%b%s>uBV$G5/F0(B

$B%3%s%F%J$N5/F0>uBV$r3NG'(B

`$ docker-compose ps`

## Jira/Confluence
[Confluence](https://qiita.com/iguchikoma/items/97128b3d3bfbbe7e71a4)

`$ docker volume create --name jiraVolume`

`$ docker run -v jiraVolume:/var/atlassian/application-data/jira --name="jira" -d -p 8080:8080 atlassian/jira-software`

`$ docker volume create --name confluenceVolume`

`$ docker run -v confluenceVolume:/var/atlassian/application-data/confluence --name="confluence" -d -p 8090:8090 -p 8091:8091 atlassian/confluence-server`

## CentOS 8
[CentOS 8$B$N%$%a!<%8%@%&%s%m!<%I!&5/F0(B](https://qiita.com/witchcraze/items/bc05f8fd90bea2dc333f)

`$ sudo docker pull centos:8`

`$ sudo docker images`

`$ sudo docker run -it --rm centos:8 /bin/bash`

&nbsp;&nbsp;&nbsp; -it : $B%3%s%F%J$NI8=`F~NO$r3+$/!"(Btty$B$r;H$&(B

&nbsp;&nbsp;&nbsp; --rm : $B<B9T40N;8e$K%3%s%F%J$r:o=|$9$k(B

