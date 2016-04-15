# Docker Swarm + Machineを使って、AWS上に開発環境を構築する


コンニチーハ、Dockerを使って幸せになれないか模索中の千葉です。

今回は、Swarmを使ってAWS上にコンテナのリソースプールを構築します。

## 解決したい課題

* チームで開発することを想定し、コンテナを常時起動させたい(ローカル端末上だと常時起動は難しい) -> AWS上に作ることで常時起動可能な環境を構築する
* 手間を掛けずに、コンテナのリソースプールを増やしたり、減らしたりしたい -> docker-machine + docker-swarmを利用することで実現
* webアクセス時にポート番号を意識しない構成

### やらないこと

* 自動でのスケールアウト、スケールダウン
* コンテナの自動フェイルオーバー

## アーキテクチャ



## 構築

### docker-machineインストール

管理用EC2インスタンス(今回はamazon linuxを使用)

```
# curl -L https://github.com/docker/machine/releases/download/v0.6.0/docker-machine-`uname -s`-`uname -m` > /usr/local/bin/docker-machine && \
chmod +x /usr/local/bin/docker-machine
```

### 



export WS_AMI=ami-b36d4edd
export WS_DEFAULT_REGION=ap-northeast-1
export WS_VPC_ID=vpc-515fdf34
export WS_ZONE=a
export WS_SUBNET_ID=subnet-8bf092fc
export WS_SECURITY_GROUP=sg_ec2-logs
export WS_TAGS=swarm
export WS_INSTANCE_TYPE=t2.nano
export WS_ROOT_SIZE=20
export WS_INSTANCE_PROFILE=chiba-ec2
export WS_SSH_USER=ubuntu
export WS_ACCESS_KEY_ID=
export WS_SECRET_ACCESS_KEY=

[bash]
$ export AWS_AMI=
$ export AWS_DEFAULT_REGION=
$ export AWS_VPC_ID=
$ export AWS_ZONE=
$ export AWS_SUBNET_ID=
$ export AWS_SECURITY_GROUP=
$ export AWS_TAGS=
$ export AWS_INSTANCE_TYPE=
$ export AWS_ROOT_SIZE=
$ export AWS_INSTANCE_PROFILE=
$ export AWS_SSH_USER=
$ export AWS_ACCESS_KEY_ID=
$ export AWS_SECRET_ACCESS_KEY=

$ docker-machine create --driver amazonec2 ¥
--swarm ¥
--swarm-master ¥
--swarm-discovery token://934afbacc9e635c52e8b6544a2eba998 ¥
swarm01

Creating CA: /root/.docker/machine/certs/ca.pem
Creating client certificate: /root/.docker/machine/certs/cert.pem
Running pre-create checks...
Creating machine...
・・・・

$ 


[/bash]


## 参考

https://docs.docker.com/machine/drivers/aws/