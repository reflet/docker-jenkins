# Jenkins + Python3

オフィシャルのjenkinsを元に調整を行いました。

### 調整内容

* locale設定 (ja.utf-8)
* タイムゾーン （Asia/Tokyo）
* 必要なツールのインストール  
※ less vim jq docker-client
* python2 (python-pip python-setuptools)
* python3 (python-pip python-setuptools)
* selenium
* fabric

### 使い方

下記のコマンドにてコンテナを起動します

```
$ docker pull reflet/docker-jenkins
$ docker run -d --name jenkins reflet/docker-jenkins
$ docker run exec -it jenkins bash
```

### 操作画面
Vagrant(192.168.33.10)を使っている場合の例です。

* http://192.168.33.10:8080

### docker-composeの記述例

```
version: '2'
services:
    jenkins:
        restart: always
        image: reflet/docker-jenkins
        container_name: 'jenkins'
        working_dir: '/root/opt'
        ports:
            - '8080:8080'
            - '50000:50000'
        volumes:
            - /var/run/docker.sock:/var/run/docker.sock
            - jenkins-data:/var/jenkins_home
  volumes:
      jenkins-data:
          driver: local
```
