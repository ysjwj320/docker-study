### docker容器的数据清理

&nbsp;&nbsp;&nbsp;&nbsp;在使用docker-compose创建和删除容器后，发现磁盘占用还是没有下降，因此，查找磁盘暂用空间最大的地方在于docker/volumes目录。

&nbsp;&nbsp;&nbsp;&nbsp;docker/volumes是容器启动时，存储运行数据的地方。

&nbsp;&nbsp;&nbsp;&nbsp;docker容器运行数据存储的方式：
* Volumes: 创建和管理都是docker容器，数据存放在docker/volumes。这种方式在使用docker-compose down掉后，数据卷不会删除。如果需要删除，可以使用docker volume prune命令
* Bind mounts: 就是我们常使用的挂载方式，使用参数--volume或--mount，直接将数据目录映射到主机。用户可以直接修改数据内容。
* tmpfs mounts: 数据保存在内存，只支持linux系统。

### 镜像清理

&nbsp;&nbsp;&nbsp;&nbsp;和volumes一样，image也同样可以通过命令docker image prune进行清理。清理的内容是没有容器使用的镜像。
