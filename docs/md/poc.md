# $B4pK\>pJs(B
$B>l=j(B : GCP GCE

# $B%5!<%S%9(B
## knowledge
$BL\E*(B: $B%J%l%C%8%Y!<%9J]4IMQ(B

$B%]!<%H(B: 8080

$B%"%/%;%9J}K!(B: Web

## Jenkins
$BL\E*(B: CI/CD PoC$B4D6-MQ(B

$B%]!<%H(B: 18080

$B%"%/%;%9J}K!(B: Web

# $B%[!<%`%G%#%l%/%H%j(B
~
<br>
&nbsp;&nbsp;&nbsp;$B(&(B docker
<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;$B(&(B docker-knowledge

# $B%$%s%9%H!<%k%Q%C%1!<%8(B
**docker-ce**
<br>
&nbsp;&nbsp;&nbsp;$B(&(B apt-transport-https
<br>
&nbsp;&nbsp;&nbsp;$B(&(B ca-certificates 
<br>
&nbsp;&nbsp;&nbsp;$B(&(B curl
<br>
&nbsp;&nbsp;&nbsp;$B(&(B software-properties-common

**docker-compose**

# $B3F<o<j=g(B

## docker$B%$%s%9%H!<%k(B

[docker$B%$%s%9%H!<%k(B(Ubuntu)](https://qiita.com/tkyonezu/items/0f6da57eb2d823d2611d)

[docker$B%$%s%9%H!<%k(B(Ubuntu 20.04LTS)](https://qiita.com/nanbuwks/items/0ba1d13b3cd27e5c6426)

$B%"%C%W%G!<%H(B

`$ sudo apt-get update`

$BA0Ds%=%U%H%&%'%"$N%$%s%9%H!<%k(B

`$ sudo apt install apt-transport-https ca-certificates curl software-properties-common`

GPG$B8x3+80$N%$%s%9%H!<%k(B

`$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -`

`$ sudo apt-key fingerprint 0EBFCD88`

apt$B%j%]%8%H%j$N@_Dj(B

`$ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"`

docker-ce$B$N%$%s%9%H!<%k(B

`$ sudo apt update`

`$ apt-cache policy docker-ce`

`$ sudo apt install docker-ce`

$B>uBV3NG'(B

`$ sudo systemctl status docker`

$B0lHL%f!<%6!<$G<B9T$G$-$k$h$&$K$9$k(B

`$ sudo usermod -aG docker <$B%"%+%&%s%HL>(B>`

## docker-compose$B$N%$%s%9%H!<%k(B
[docker-compose$B$N%$%s%9%H!<%k(B](https://docs.docker.com/compose/install/)

docker-compose$B$N:G?7HG$r%@%&%s%m!<%I(B

`$ sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose`

$B%Q!<%_%C%7%g%s$rIUM?$7!"%Q%9$N%7%s%\%j%C%/%j%s%/$rDI2C(B

`$ sudo chmod +x /usr/local/bin/docker-compose`

`$ sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose`

$B%P!<%8%g%s$r3NG'(B

`$ docker-compose --version`
