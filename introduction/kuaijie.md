# Cube 机型配置

当前 Cube 容器实例**已全面升级快杰版**，底层采用最新 AMD 及 Intel 服务器，支持 SSD 云盘。

|分类|宿主资源|
|---|---|
|计算|Intel Cascadelake CPU（2.5GHz主频）<br>AMD 第二代 EPYC CPU（2.9GHz 主频） |
|存储|SSD UDisk|
|网络|25G 以太网|

## CPU / 内存配置

如通过控制台创建 Cube 实例，实例中单个 Container 支持如下 CPU / 内存规格配置：

| CPU | 内存 |
|-----|-----|
|100m|128Mi|
|500m|512Mi/1Gi/2Gi|
|1|1Gi/2Gi/4Gi|
|2|2Gi/4Gi/8Gi|
|4|4Gi/8Gi/16Gi|
|8|8Gi/16Gi/32Gi|
|16|16Gi/32Gi/64Gi|
|32|32Gi/64Gi/128Gi|

如通过 API 创建，除以上规格外，Container CPU 配置支持 1 - 32 的任一整数核数，但 CPU:内存比例需满足 1:1/2/4，如 3C3G / 3C6G / 3C12G。

每个 Cube 实例总资源最大支持 32C128Gi。
