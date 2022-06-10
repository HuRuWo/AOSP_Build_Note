### 下载源码编译相关环境

#### 安装open-jdk

```
sudo apt install openjdk-8-jdk-headless
```

验证

```
huruwo@ubuntu:~$ java -version
openjdk version "1.8.0_312"
OpenJDK Runtime Environment (build 1.8.0_312-8u312-b07-0ubuntu1~18.04-b07)
OpenJDK 64-Bit Server VM (build 25.312-b07, mixed mode)
```
###


### 进行编译步骤


#### 设置编译环境

进入repo目录

运行

```
source ~/bin/build/envsetup.sh
```

#### 选择编译版本


还是在bin目录下 输入lunch

![f9dd05a9234ba73efa852f62f7be49b7.png](en-resource://database/2070:1)

要想找到适配手机的版本


看这个页面

https://source.android.google.cn/setup/build/running?hl=zh-cn


![a6c81d9caa043be0965473bd61735af7.png](en-resource://database/2072:1)

对应的就是第三个

```
 3. aosp_blueline-userdebug
```

输入3

现在你的环境就切换到了编译pixel3的分支了

#### 导入手机驱动文件

以pixel3为例

先去

[https://source.android.google.cn/setup/start/build-numbers?hl=zh-cn](https://source.android.google.cn/setup/start/build-numbers?hl=zh-cn)


找到 android-10.0.0_r30 的版本代号

![35047b1d95a9181e6c3cba986486b982.png](en-resource://database/2074:1)

就是 QQ2A.200305.002


再去

[https://developers.google.com/android/drivers](https://developers.google.com/android/drivers)

![9eca0a507d7d3b47236bbe4d766f0521.png](en-resource://database/2076:1)

下载这两个文件 解压导出 放到工程根目录下

![96d35a4dfc571771f82959b88c07e59a.png](en-resource://database/2078:1)


![4f4df86bc39e853e0c62a91b0d2e9a21.png](en-resource://database/2080:1)

```
./extract-google_devices-blueline.sh 
./extract-qcom-blueline.sh
```

有个同意证书的东西

都在 8 e 结束

需要输入 I ACCEPT

![b966b731d4111fa6a22e9c3ed1a31672.png](en-resource://database/2082:1)


#### 编译

```
make -j8
```

![6535fc2a1e145b1dbb741e2f61288ff5.png](en-resource://database/2084:1)


### 问题

#### 错误1


运行 source ~/bin/build/envsetup.sh 没反应

他就是没反应的 只要不报错就行


852QLDV824A6J


#### 错误2

```
02:54:49 ninja failed with: exit status 1
build/make/core/main.mk:21: recipe for target 'run_soong_ui' failed
make: *** [run_soong_ui] Error 1
```

解决方法

在make之前执行下面操作 export LC_ALL=C