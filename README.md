KAFKA
=========

通过 ansible 部署在容器下运行的 Kafka 服务。

Installation
------------

`ansible-galaxy install gengxiankun.zookeeper`

Role Variables
--------------

variable | description
------------ | -------------
OPT_PATH | 部署目录
SRV_PATH | 服务运行时持久化目录
KAFKA_DEPLOYMENT_MODE | kafka 部署模式，PseudoDistributed、FullyDistributed
KAFKA_NODE_NUM | kafka 节点数
KAFKA_IMAGE_TAG | kafka 镜像版本
KAFKA_ADVERTISED_HOST_NAME | kafka advertised.host.name ，外网访问 IP
KAFKA_ZOOKEEPER_CONNECT | 连接 zokeeper 服务配置
KAFKA_PORT | kafka 对外提供服务端口号
KAFKA_NETWORK | 依赖的容器网络

Dependencies
------------

- docker
- zookeeper

Example Playbook
----------------

    - hosts: servers
      roles:
        - gengxiankun.kafka
      vars: 
        - OPT_PATH: /opt
        - SRV_PATH: /data/runtime
        - KAFKA_DEPLOYMENT_MODE: PseudoDistributed
        - KAFKA_NODE_NUM: 3
        - KAFKA_IMAGE_TAG: latest
        - KAFKA_ADVERTISED_HOST_NAME: 127.0.0.1
        - KAFKA_ZOOKEEPER_CONNECT: zookeeper_1:2181, zookeeper_2:2181, zookeeper_3:2181
        - KAFKA_PORT: 9092
        - ZOOKEEPER_NETWORK: zookeeper

License
-------

BSD

Author Information
------------------

This role was created in 2019 by Xiankun Geng, Learn more about the author's role in [galaxy](https://galaxy.ansible.com/gengxiankun).
