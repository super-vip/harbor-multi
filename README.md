# harbor
提供官方Harbor amd64与自编译arm64镜像

[Arm编译源码](https://gitlab.ayou.ink/IabSDocker/Harbor)

|![notification](https://raw.githubusercontent.com/goharbor/website/master/docs/img/readme/bell-outline-badged.svg)Community Meeting|
|------------------|
|The Harbor Project holds bi-weekly community calls in two different timezones. To join the community calls or to watch previous meeting notes and recordings, please visit the [meeting schedule](https://github.com/goharbor/community/blob/master/MEETING_SCHEDULE.md).|

</br> </br>

<img alt="Harbor" src="https://raw.githubusercontent.com/goharbor/website/master/docs/img/readme/harbor_logo.png">

>amd镜像由[Harbor官方releases页面而来](https://github.com/goharbor/harbor/releases/)

>arm镜像由[IabSDocker修改部分官方源码中的文件而来](https://gitlab.ayou.ink/IabSDocker/Harbor)对于核心源码并没有改动，只是对于在arm环境执行 `make package_offline` 打包命令时的报错对部分Makefile、Dockerfile.base进行了修改

# 食用方法二选一
## 一、以安装harbor v2.12.0为例
```
wget https://github.com/IabSDocker/harbor/releases/download/v2.12.0/harbor-offline-installer-v2.12.1_amd64.tgz
以正常方式安装Harbor ARM64 Version
tar xf harbor-offline-installer-v2.12.0.tgz
cd harbor
cp harbor.yml.tmpl harbor.yml
修改harbor.yml文件内容
./install.sh
```

## 二、以安装harbor v2.12.0为例
下载离线镜像包
```
docker pull iabsdocker/harbor:v2.12.0
```
创建一个新的容器实例
```
HARBOR_ID=$(docker create iabsdocker/harbor:v2.12.0 /bin/true)
```
从容器中拷贝文件
```
docker cp $HARBOR_ID:harbor-offline-installer-v2.12.0.tgz ./harbor-offline-installer-v2.12.0.tgz
```
删除容器实例
```
docker rm $HARBOR_ID
```
以正常方式安装Harbor ARM64 Version
```
tar xf harbor-offline-installer-v2.12.0.tgz
cd harbor
cp harbor.yml.tmpl harbor.yml
```
修改harbor.yml文件内容
```
./install.sh
```
