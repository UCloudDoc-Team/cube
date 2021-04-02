# 自建镜像仓库支持

容器镜像封装了应用代码，是用户的重要资产之一，处于强安全性的考虑，部分用户在容器应用的使用过程中，有使用自建镜像仓库的需求。
Cube 支持拉取同一 VPC 下的自建镜像仓库，丰富了使用场景，确保用户镜像和代码安全。

## 控制台创建 / 修改 Cube 实例

在控制台创建/修改 Cube 及 Deployment 时，在容器「镜像设置」页面，选择自建镜像仓库，并输入镜像的详细信息。当前只支持基于 UCloud 同一主账号下云主机搭建的镜像仓库。

|字段|说明|
|:----|:----|
|镜像地址|包含镜像名及版本号的完整镜像拉取地址，如 core.harbor.domain/nginx:latest|
|所属 VPC|自建镜像仓库所在 VPC，如 VPC 在同一项目下，可直接选择，如存在跨项目情况，需要输入对应的 VPC ID，如 uvnet-xxxxxxxx|
|仓库域名|仓库域名，如 core.harbor.domain|
|仓库地址|仓库所在云主机的内网 IPv4 地址，如 10.9.87.17|
|用户名|镜像仓库用户名，非必填|
|密码|镜像仓库密码，非必填|

其他创建流程均不变，请参考[快速创建](/cube/userguide/quick_start.md)及[创建详解](cube/userguide/describe_create.md)

## API 创建 / 修改 Cube 实例

在通过 API 创建 / 修改 Cube 及 Deployment 时，需要在相应的 pod yaml 文件中 spec 字段下添加 imagePullSecrets 字段，如下：

```yaml
spec
  containers:
  imagePullSecrets:
  - username: 'zth'                       # 镜像仓库用户名，非必填
    password: 'Harbor'                    # 镜像仓库密码，非必填
    registryserver: 'core.harbor.domain'  # 镜像仓库域名
    registryaddr: '10.9.87.17'            # 仓库所在云主机的内网 IPv4 地址
    vpcId: 'uvnet-xxxxxxxx'               # 自建镜像仓库所在 VPC 的 VPC ID
```

详细 API 请参照[Cube API 文档](/api/cube-api/README.md)