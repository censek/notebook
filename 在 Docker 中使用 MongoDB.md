> [安装 Docker](https://blog.csdn.net/Bule_daze/article/details/96281157)

#### 1. 下载镜像
```shell
docker search mongodb  #在Docker的镜像中查询MongoDB的镜像
docker pull mongo      #拉取官方mongo镜像（一般为第一个）
```



##### 🦄️ 一些命令：
- `docker images`：列出本地主机上的镜像。

	> 各选项说明：
	> - REPOSITORY：表示镜像的仓库源
	> - TAG：镜像的标签
	> - IMAGE ID：镜像ID
	> - CREATED：镜像创建时间
	> - SIZE：镜像大小
	
- `docker ps`：列出容器
	> **docker ps [OPTIONS]**  参数说明：
	> - -a：显示所有的容器，包括未运行的。
	> - -f：根据条件过滤显示的内容。
	> - --format：指定返回值的模板文件。
	> - -l：显示最近创建的容器。
	> - -n：列出最近创建的n个容器。
	> - --no-trunc：不截断输出。
	> - -q：静默模式，只显示容器编号。
	> - -s：显示总的文件大小。

<br>

#### 2. 运行容器
`docker run 容器ID`
```shell
 docker run -h mqj -p 27017:27017 -v $PWD/db:/data/db --name mongodb-censek cdc6740b66a7
 ```
 > **docker run [OPTIONS] IMAGE [COMMAND] [ARG...]**  参数说明：
 > - -u：指定容器的用户
 > - -v：给容器挂载存储卷，挂载到容器的某个目录
 > -  -d：指定容器运行于前台还是后台，默认为 false
 > - -w：指定容器的工作目录
 > - -m：指定容器的内存上限
 > - -p：指定容器暴露的端口，格式为：`主机(宿主)端口:容器端口`
 > - -P：随机映射一个 49000~49900 的端口到内部容器的网络端口。
 > - -h：指定容器的主机名
 > - --dns：指定容器的dns服务器
 > - --network host 指定与宿主机的网络链接方式
// 默认是 bridge，即桥接网络，以桥接模式连接到宿主机；host 是宿主网络，即与宿主机共用网络；none 则表示无网络，容器将无法联网。
 > - --restart="no" 容器停止后的重启策略  no：不重启；on-failure：容器故障退出（返回值非零）时重启；always：容器退出时总是重启 。
 > <br>
 > 
 > 🔗[docker run, –name, –hostname 和 –rm 详解](http://www.dockerinfo.net/3689.html)

<br>

#### 3. 开始使用
mongodb 容器运行起来后（`docker ps` 可以查看到的时候），可直接在可视化界面中进行操作，如果想在终端操作：
`docker exec -it 容器ID /bin/bash`
> - -d：分离模式: 在后台运行
> - -i：即使没有附加也保持STDIN 打开
> - -t：分配一个伪终端
```shell
docker exec -it ca5ea3582c0d bash    
#或者`docker exec -it ca5ea3582c0d /bin/bash`

mongo  #进入MongoDB shell 端
```
<br>

#### 4. 退出与再次使用
每次不用 MongoDB 想要退出的时候，`docker stop 容器ID` 停止运行中的容器，下次再想用的时候使用 `docker start 容器ID` 命令。
> `docker ps` 可以查看到，便可直接在可视化界面操作MongoDB。
```shell
docker stop 08fcce825138
docker start 08fcce825138

# docker start :启动一个或多个已经被停止的容器
# docker stop :停止一个运行中的容器
# docker restart :重启容器
```
<br>

#### 5. 如果想把本地 MongoDB 数据库中数据迁移到 Docker 中
###### 1⃣️ [导出本地主机 MongoDB 数据库 json 文件](https://blog.csdn.net/Bule_daze/article/details/100704018)。
###### 2⃣️ 使用 cp 命令将主机文件拷贝到 Docker 容器中
`docker cp 导出的数据的文件名 容器ID:/`
###### 3⃣️ 进入容器。
`docker exec -it 容器ID /bin/bash`
###### 4⃣️ 执行导入命令。（需要先在 Docker 中的 MongoDB 中创建目标数据库）
`mongorestore -d 目标数据库名 想要导入的数据的文件路径`
```shell
docker cp eportalplus 08fcce825138:/
docker exec -it 08fcce825138 /bin/bash
mongorestore -d eportal eportalplus
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200106152811355.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L0J1bGVfZGF6ZQ==,size_16,color_FFFFFF,t_70)
> 注： 可以看到左上角 `root@mqj` ，mqj 就是我在步骤 **2.运行容器** 中通过 -h 指定的容器的主机名<br><br>
> - （其它比如只导入某个集合的数据的命令见上方 1⃣️ 中链接。）
