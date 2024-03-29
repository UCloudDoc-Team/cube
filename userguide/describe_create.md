# 创建详解

通过上面的快速创建我们接下来将通过上面的例子来进行创建操作中的详细设置说明。如果您对于kubernetes比较熟悉，可以查看[k8s参考示例对比](/cube/userguide/from_k8s.md)

## 卷设置

#### 非必填项

卷设置提供了 config 类型、UDisk 云盘挂载（[在 Cube 中使用 UDisk](/cube/volume/udisk.md)）、NFS 文件存储挂载（[在 Cube 中使用 UFS](/cube/volume/ufs.md)）及 emptyDir 类型。
config 类型与Kubernetes中的configMap资源对象一致，提供的是键值对配置文件挂载。

![](../images/volume/config1.png)

如图所示点击添加卷设置，填入如下信息然后确定。

卷名：`defaultconf`

键值对key：`default.conf`

键值对value：
```
    server {
        listen      8080; 
        server_name localhost; 
        location / {
            root   /usr/share/nginx/html; 
            index  index.html index.htm; 
        } 
        error_page   500 502 503 504  /50x.html; 
        location = /50x.html { 
            root   /usr/share/nginx/html; 
        }
      }
```

这里可以看到我们修改了nginx的配置文件，将监听端口配置从原80到8080，作为一个配置文件进行创建。

> 这里只会创建一个卷设置，将不会进行挂载，如需挂载需要在高阶设置中进行卷挂载。

## 高阶设置

高阶设置中将针对容器进行详细的参数设置。

![](../images/advanced1.png)

### 工作目录(workDir)

#### 非必填项

这里可以定义容器运行时的工作目录，指定了工作目录之后镜像中所有命令执行都将在工作目录中完成，可以将工作目录指定在Dockerfile中。这里我们使用到的nginx工作目录为根目录。

工作目录: `/`

### 命令(command)

#### 非必填项
  
这里可以定义容器运行时的命令，命令对应的是镜像中程序运行的命令，如果没有设置，将使用容器镜像中的命令。

### 参数(args)

#### 非必填项  

这里可以定义容器运行命令时的参数，如果没有设置，将使用容器镜像中的命令。从Dockerfile中可以看到nginx的参数全部放在了命令中，我们也可以将它拆分成为命令和参数。

这里我们使用到的nginx命令在Dockerfile中为`CMD ["nginx", "-g", "daemon off;"]`，其中可以拆分成

命令(command): 
```
nginx
```

参数(args): 
```
-g
daemon off;
```


### 环境变量

#### 非必填项

这里可以定义容器运行时的环境变量，环境变量将在运行的容器中使用`env`进行查看，可以将环境变量指定在Dockerfile中。这里我们使用的nginx环境变量可以参考Dockerfile中的环境变量。

环境变量name: `NGINX_VERSION`

环境变量value: `1.17.10`

### 挂载卷

#### 非必填项

这里可以将我们创建的卷设置进行挂载，我们上面创建了一个nginx的配置文件config，这里我们将它挂进我们的容器中。
  
挂载路径: `/etc/nginx/conf.d/`

卷名称: `defaultconf`

> 注意：如没有创建卷设置，在挂载卷中将选择不到具体的卷名称，请先创建卷设置。

## 标签

#### 非必填项

这里可以将我们创建的Cube实例打上标签，可以方便我们后续通过标签进行筛选，如下举例。

标签key: `app`

标签value: `nginx`

## 重启策略

这里可以设置我们创建的Cube实例的重启策略，分别为总是(Always)、失败时(OnFailure)、从不(Never)。

## 自定义 DNS 服务及 HostAliases

为 Cube 实例添加自定义 DNS 服务，如无需自定义，则默认使用 UCloud 内网 DNS 地址；当 DNS 配置不合理的时候，可以通过通过 HostAliases 字段向 Cube 实例的 /etc/hosts 文件中添加条目， 覆盖对主机名的解析。 

![](../images/createCube4.png)

## 自定义网络

* 您所创建的Cube实例的网络位置将存在于具体的一个VPC的子网里。
* 您可以根据您镜像程序的需要选择是否绑定外网IP和选择对应的防火墙设置。