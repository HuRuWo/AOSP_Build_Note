### 下载同步repo源码

纯净的ubuntu环境编译ASOP完成步骤

#### 1.安装repo

repo:管理多个git项目的项目管理工具

```
sudo apt install repo
```
#### 2.安装curl
curl:下载工具

```
sudo apt-get install curl
```

#### 3.下载全局repo配置文件

参考 https://mirrors.tuna.tsinghua.edu.cn/help/AOSP/

```

mkdir ~/bin
PATH=~/bin:$PATH
curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
chmod a+x ~/bin/repo
```

下载完成检测

```
huruwo@ubuntu:~/bin$ ls
repo
```

#### 4.设置更新镜像地址

```
sudo gedit ~/.bashrc
```
新增代码

```
# repo 
export REPO_URL='https://mirrors.tuna.tsinghua.edu.cn/git/git-repo/'
```
配置生效
```
source ~/.bashrc
```

![599c69079316046551daba98c6bfc61f.png](en-resource://database/1886:1)


#### 5.配置git config信息

```
  git config --global user.email "1458476478@qq.com"
  git config --global user.name "huruwo"
```

#### 6.查询适配的系统版本 初始化repo

https://source.android.com/setup/start/build-numbers#source-code-tags-and-builds

![deda6924d9dbfb70dcb2bd25548eda0f.png](en-resource://database/1888:1)


选择  android-10.0.0_r30 进行下载编译

```
python3 ~/bin/repo init -u https://mirrors.tuna.tsinghua.edu.cn/git/AOSP/platform/manifest -b android-10.0.0_r30
```

初始化仓库 不要很久

#### 7.同步代码

耗时最久 还容易失败的操作

```
python3 ~/bin/repo sync
```

### 编译

#### 1.安装open jdk

```
sudo apt install openjdk-8-jdk-headless
```



## 相关报错以及解决

