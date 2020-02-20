# 脚本功能
[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)
  - 项目基于Flask框架
  - 项目基于subconverter：https://github.com/tindy2013/subconverter
  - 配置文件版示例： https://github.com/lzdnico/subconverteriniexample
  - 项目示例站点： https://subweb.niconewbeee.tk
  - 托管地址生成页面示意图
  ![image](https://github.com/lzdnico/subweb/blob/test/images/index.png) 
# 环境搭建及运行
  - 1.安装python3 依赖： 
  ```bash
  apt install -y python3-pip  git python3
  ```
  - 2.下载源码：
  ```bash
  cd 
  git clone https://github.com/lzdnico/subweb.git 
  ```
  - 3.安装库： 
  ```bash
  cd subweb
  pip3 install -I -r requirements.txt 
  ```
  - 4.开始运行：
  ```bash
  chmod 777 /root//subweb/subweb.sh
  cd /root/subweb 
  ./subweb.sh 
  ```
  - 5.登陆管理页面：登陆地址：http://ip:10086/admin             

    首先修改前后端地址以及管理员密码，在内容框复制：

```bash  
#全局变量定义
aff = '不限制机场，规则生成失败，请检测调用格式。STC测试可用，注册地址：bilibili.stchk.cloud/auth/register?code=gzI5'   
subip = 'http://127.0.0.1:10010'      #默认apiip 是web的端口，在api.py的main函数指定，或者docker的端口指定。  默认subip是 subconverter 的端口，在config/perf.ini 中指定，或者docker的端口指定。
apiip = 'http://127.0.0.1:10086'      #套CDN后，可以在服务器上整反代，将域名反代到本地运行的端口：http://127.0.0.1:10010 
passwd = 'admin'
```

     在地址框复制：

```bash
../api/aff.py
```

    管理员密码默认为admin。点击上传，然后点击重启前端（需要再次输入密码）。然后经过最长1分钟后，就能正常使用了。

    ！！！一定要修改config/pref.ini里的【api_access_token】，以及【managed_config_prefix】

# Docker 运行 By NicoNewBeee 
  - 1.安装Docker运行环境： 
  ```bash
  docker pull niconewbeee/subweb:basic
  ```
  - 2.下载源码：
  ```bash
  cd 
  git clone https://github.com/lzdnico/subweb.git 
  ```
  - 3.客制化：
  ```bash 
  chmod 777 /root/subweb/config/subconverter                  修改后端权限
  chmod 777 /root/subweb/docker.sh                            修改启动脚本权限
  ```
  - 5.开始运行：
  -p 前端端口号：10086 -p 后端端口号：10010                      这个前/后端端口号需要与api/aff.py中的一致
  ```bash 
  docker run  -d --name=subweb  --privileged=true --restart=always -v /root/subweb:/subweb -p 10086:10086 -p 10010:10010  niconewbeee/subweb:basic
  ```
  - 6.登陆管理页面

    用法看 环境搭建及运行 第5步

  - 7.查看日志 
```bash
docker logs -f -t --tail 10 subweb
```
- 8.停止 
```bash
docker stop subweb
```
- 9.重启 
```bash
docker restart subweb
```
- 10.删除 
```bash
docker rm -f subweb
```

- 11.如何同步最新源码 
```bash
rm -rf /root/subweb
重复2，3，9，6
或者看看docker/update.sh 找找灵感？
```

# Docker 运行 By du5 (旧版)
> https://docker.io/gtary/subweb build by [@du5](https://t.me/Gtary)
1. 拉取镜像
```bash
docker pull gtary/subweb
```
2. 运行 
```bash
docker run -d --restart=always --name=subweb -e WEB_HOST=http://127.0.0.1:Web_Port -e CORE_HOST=http://127.0.0.1:Core_Port -p Web_Port:10086 -p Core_Port:10010 gtary/subweb
```
3. 停止
```bash
docker stop subweb
```
4. 重启
```bash
docker restart subweb
```
4. 删除
```bash
docker rm -f subweb
```
5. 查看日志
```bash
docker exec subweb tail /var/log/core.log -f
docker exec subweb tail /var/log/web.log -f
```
# 联系我
  - 更新频道：https://t.me/niconewbeeeapi
  - 打赏地址:https://t.me/niconewbeeeapi/134

[//]: # (These are reference links used in the body of this note and get stripped out when the markdown processor does its job. There is no need to format nicely because it shouldn't be seen. Thanks SO - http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax)


   [dill]: <https://github.com/joemccann/dillinger>
   [git-repo-url]: <https://github.com/joemccann/dillinger.git>
   [john gruber]: <http://daringfireball.net>
   [df1]: <http://daringfireball.net/projects/markdown/>
   [markdown-it]: <https://github.com/markdown-it/markdown-it>
   [Ace Editor]: <http://ace.ajax.org>
   [node.js]: <http://nodejs.org>
   [Twitter Bootstrap]: <http://twitter.github.com/bootstrap/>
   [jQuery]: <http://jquery.com>
   [@tjholowaychuk]: <http://twitter.com/tjholowaychuk>
   [express]: <http://expressjs.com>
   [AngularJS]: <http://angularjs.org>
   [Gulp]: <http://gulpjs.com>

   [PlDb]: <https://github.com/joemccann/dillinger/tree/master/plugins/dropbox/README.md>
   [PlGh]: <https://github.com/joemccann/dillinger/tree/master/plugins/github/README.md>
   [PlGd]: <https://github.com/joemccann/dillinger/tree/master/plugins/googledrive/README.md>
   [PlOd]: <https://github.com/joemccann/dillinger/tree/master/plugins/onedrive/README.md>
   [PlMe]: <https://github.com/joemccann/dillinger/tree/master/plugins/medium/README.md>
   [PlGa]: <https://github.com/RahulHP/dillinger/blob/master/plugins/googleanalytics/README.md>
