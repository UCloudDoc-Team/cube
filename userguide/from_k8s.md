# k8s参考示例对比

如果您对于kubernetes比较熟悉，可以查看对比Cube参数与Kubernetes中的对照关系。


```
## 卷设置/ConfigMap
apiVersion: v1
kind: ConfigMap
metadata:
  name: defaultconfig  # 卷名
data:
  default.conf: |      # 键值对key: value
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
---
## Cube实例
apiVersion: v1
kind: Pod
metadata:
  name: cube            # 容器组名称
  labels:
    app: nginx          # 标签key: value
spec:
    containers:
    - name: cube01      # 容器名称
      image: uhub.service.ucloud.cn/ucloud/nginx:1.17.10-alpine  #容器镜像
      env:
      - name: NGINX_VERSION   # 容器环境变量name: value
        value: 1.17.10
      workingDir: /           # 工作目录
      command: ["nginx"]      # 命令
      args: ["-g", "daemon off;"]  # 参数
      ports:
      - name: http
        containerPort: 8080
      volumeMounts:          # 挂载卷
      - name: nginx-defaultconfig
        mountPath: /etc/nginx/conf.d/
    volumes:
    - name: nginx-defaultconfig
      configMap:
        name: defaultconfig
```