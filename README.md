# AndroidNAS
这个项目旨在将闲置安卓设备打造为NAS
This project aims to transform idle Android devices into NAS

目前先记录我在探索过程中获取到的各种知识，之后将这个项目全英文化并邀请更多人参与进来
Currently, I am documenting the various knowledge I have gained during the exploration process. Afterwards, I plan to internationalize this project and invite more people to participate.

这个项目不排除收费方案，因为这其中有很多工作都是很有价值的，但尽量只选择那些质量优秀的无广告方案记录在本项目中
This project does not rule out the possibility of a paid plan, as there is valuable work involved. However, we will strive to include only high-quality, ad-free solutions in this project.

# 技术选型
## 如何在安卓设备跑起NAS服务
按复杂度排序：
### 1. 使用能搭建web服务的app
#### KSWEB（收费，2美刀，试用期5天）
官网：[https://sspai.com/post/57699](https://www.kslabs.ru/)
KSWEB标准版内置lighttpd+php+mysql，专业版包括nginx、apache等组件。内置no-ip，可直接配置ddns，自定义二级域名，每次有效期30天

多app
https://sspai.com/post/71543

### 2. 在termux下搭建web服务
1. 安装termux
2. 自行安装web服务套件，例如nginx+php+mysql等
3. 通过FTP、SMB等进行文件同步

### 3. 在termux下通过qemu虚拟全功能linux跑docker
https://github.com/BigWanGa/docker-in-termux
全能性最高，过程不算很复杂，性能低，待测试性能对比
宿主机目录挂载：
[https://wiki.archlinuxcn.org/wiki/QEMU#%E5%AE%BF%E4%B8%BB%E6%9C%BA%E5%92%8C%E8%99%9A%E6%8B%9F%E6%9C%BA%E6%95%B0%E6%8D%AE%E4%BA%A4%E4%BA%92](https://wiki.archlinuxcn.org/wiki/QEMU#%E5%AE%BF%E4%B8%BB%E6%9C%BA%E5%92%8C%E8%99%9A%E6%8B%9F%E6%9C%BA%E6%95%B0%E6%8D%AE%E4%BA%A4%E4%BA%92)
https://zhuanlan.zhihu.com/p/55025102

### 4. root后通过linux deploy运行docker
https://github.com/meefik/linuxdeploy

### 5. 重新编译手机固件，开启缺失功能，让系统原生支持docker
https://gist.github.com/FreddieOliveira/efe850df7ff3951cb62d74bd770dce27#2-building
性能和全能性最高，过程最复杂且不通用（需要有安卓设备的完整开源ROM）
https://zhuanlan.zhihu.com/p/467521410

## 如何在外网访问安卓设备中的NAS服务
xray + ngnix
alpine的xray服务脚本https://github.com/XTLS/alpinelinux-install-xray/blob/main/init.d/xray



## NAS服务的构成
web:
- lomorage：https://docs.lomorage.com/zh/docs/Installation/lomorage-service/installation-ubuntu/
- https://sspai.com/post/57699
- nextcloud
- samba+transmission+aria2: https://zhuanlan.zhihu.com/p/65451827
- 荔枝相册：https://github.com/LycheeOrg/Lychee

docker:
- Photoprism+MariaDB+Photosync：https://post.smzdm.com/p/awz3249k/
- Photoprism: https://zhuanlan.zhihu.com/p/555552575
- immich: https://github.com/imagegenius/docker-immich/
- MTPhotos(收费，一年25，永久99): https://mtmt.tech/docs/start/install
- https://zhuanlan.zhihu.com/p/138254689

app:
- photosync(免费版有广告，900日元买断): https://www.photosync-app.com/home
- Pho（高级版1050日元，提供加密、并行上传、自定义上传、识别相机相册功能）: https://github.com/fregie/pho
  - SMB/WEBDAV/NFS/百度盘


# 实现步骤
1. 
