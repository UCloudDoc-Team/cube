## 创建三个 config 类型的卷

1. jupyter
key：jupyter_notebook_config.py
value：
```sh
c.NotebookApp.token = 'yourtoken'
```

2. us3fsconf  
key: us3fs.conf
value:
```sh
bucket: jupyter-notebook
access_key: TOKEN_cdd1f9ea-64b0-4969-aa3d-25bcb205bab3
secret_key: a3234ae8-adb7-4903-820f-d8b44ec3ba7d
endpoint: ufile.cn-north-02.ucloud.cn
```

3. us3fssh
key: us3fs.sh
value:
```sh
curl -o us3fs http://ufile-release.cn-bj.ufileos.com/us3fs%2Fus3fs
mkdir /tf/ucloud-test
chmod 777 us3fs
chmod 777 /etc/us3fs/us3fs.conf
./us3fs -f jupyter-notebook /tf/ucloud-test
```

## 创建 Cube

指定镜像为 tenserflow:latest-jupyter

* jupyter，挂载路径：/root/.jupyter/jupyter_notebook_config.py，子路径：jupyter_notebook_config.py
* us3fsconf，挂载路径：/etc/us3fs/us3fs.conf，子路径：us3fs.conf
* us3fssh，挂载路径：/root/us3fs.sh，子路径：us3fs.sh

## 创建时选择同时创建外网 EIP

实例 running 之后，eip:8888 已经可以看到 jupyter notebook，但是 us3 还没有完成挂载
在 cube 详情页，登录容器，执行 sh /root/us3fs.sh 命令，即可完成挂载

us3 挂载比较繁琐，暂时没有想到好的办法