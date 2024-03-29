# 概览

容器实例（Cube）是UCloud提供的serverless容器实例服务，通过UCloud的基础设施资源为业务提供了更加弹性、更加安全、更加快速的资源支撑，你可以在Cube上部署、管理你的容器应用，而你无需关心应用底层的服务器运维工作。
<br>



#### [产品介绍](#产品介绍)   |   [使用指南](#使用指南) |  [Deployment控制器](#Deployment控制器)  [卷设置](#卷设置)  |  [常见问题](#常见问题)


## 产品介绍

容器实例（Cube）将带大家进入一个全新的云原生程序的部署方式，首先我们来一起了解一下Cube是什么、它的优势是什么。

* [什么是Cube](/cube/introduction/whatiscube.md)
* [产品优势](/cube/introduction/advantages.md)
* [Cube 机型配置](/cube/introduction/kuaijie.md)
* [计费说明](/cube/introduction/charge.md)

## 使用指南

接下来我们使用容器实例(Cube)发布您的服务，将介绍具体创建填写字段含义以及示例操作。

* [使用须知](/cube/userguide/before_start.md)
<!--* [CPU平台](/cube/userguide/machine_type.md)-->
* [快速创建](/cube/userguide/quick_start.md)
* [创建详解](/cube/userguide/describe_create.md)
* [自建镜像仓库支持](/cube/userguide/self_repository.md)
* [第三方镜像仓库支持](/cube/userguide/external_repository.md)
* [对比K8S](/cube/userguide/from_k8s.md)

## Deployment控制器

通过 Deployment 控制器，进行 Cube 实例的批量创建和管理。

* [批量创建Cube实例](/cube/deployment/deployment_create.md)

## 卷设置

在您部署容器组时，根据应用需要，部分数据需要持久化存储，您可以参考以下文档在Cube中使用UCloud的存储资源进行挂载。

* [在Cube中使用Config](/cube/volume/config.md)
* [在Cube中使用UFS](/cube/volume/ufs.md)
* [在Cube中使用UDisk](/cube/volume/udisk.md)

## 快速入门

* [创建带SSH服务的CentOS容器](/cube/quickstar/centos_ssh.md)
* [PHP应用的高可用部署](/cube/quickstar/php.md)

## 常见问题

在您部署容器组时，对应的您可能会遇到一些使用中的问题，常见问题分类将解决您遇到的大部分问题，如您未找到解决方案请与我们客服联系。

* [运行状态](/cube/question/status.md)
* [容器重启策略](/cube/question/restart_policy.md)
