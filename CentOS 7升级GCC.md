# CentOS 7升级GCC

### 目录：

- [CentOS 7升级GCC](https://huaweicloud.csdn.net/6356103fd3efff3090b596c1.html?spm=1001.2101.3001.6650.2&utm_medium=distribute.pc_relevant.none-task-blog-2~default~BlogCommendFromBaidu~activity-2-121569398-blog-85287599.235^v29^pc_relevant_default_base3&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2~default~BlogCommendFromBaidu~activity-2-121569398-blog-85287599.235^v29^pc_relevant_default_base3&utm_relevant_index=3#CentOS_7GCC_0)
- - [基本执行步骤：](https://huaweicloud.csdn.net/6356103fd3efff3090b596c1.html?spm=1001.2101.3001.6650.2&utm_medium=distribute.pc_relevant.none-task-blog-2~default~BlogCommendFromBaidu~activity-2-121569398-blog-85287599.235^v29^pc_relevant_default_base3&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2~default~BlogCommendFromBaidu~activity-2-121569398-blog-85287599.235^v29^pc_relevant_default_base3&utm_relevant_index=3#_23)
  - - [1. 切换用户：](https://huaweicloud.csdn.net/6356103fd3efff3090b596c1.html?spm=1001.2101.3001.6650.2&utm_medium=distribute.pc_relevant.none-task-blog-2~default~BlogCommendFromBaidu~activity-2-121569398-blog-85287599.235^v29^pc_relevant_default_base3&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2~default~BlogCommendFromBaidu~activity-2-121569398-blog-85287599.235^v29^pc_relevant_default_base3&utm_relevant_index=3#1__24)
    - [2. 安装centos-release-scl：](https://huaweicloud.csdn.net/6356103fd3efff3090b596c1.html?spm=1001.2101.3001.6650.2&utm_medium=distribute.pc_relevant.none-task-blog-2~default~BlogCommendFromBaidu~activity-2-121569398-blog-85287599.235^v29^pc_relevant_default_base3&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2~default~BlogCommendFromBaidu~activity-2-121569398-blog-85287599.235^v29^pc_relevant_default_base3&utm_relevant_index=3#2_centosreleasescl_31)
    - [3. 安装devtoolset：](https://huaweicloud.csdn.net/6356103fd3efff3090b596c1.html?spm=1001.2101.3001.6650.2&utm_medium=distribute.pc_relevant.none-task-blog-2~default~BlogCommendFromBaidu~activity-2-121569398-blog-85287599.235^v29^pc_relevant_default_base3&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2~default~BlogCommendFromBaidu~activity-2-121569398-blog-85287599.235^v29^pc_relevant_default_base3&utm_relevant_index=3#3_devtoolset_40)
    - [4. 激活对应的devtoolset:](https://huaweicloud.csdn.net/6356103fd3efff3090b596c1.html?spm=1001.2101.3001.6650.2&utm_medium=distribute.pc_relevant.none-task-blog-2~default~BlogCommendFromBaidu~activity-2-121569398-blog-85287599.235^v29^pc_relevant_default_base3&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2~default~BlogCommendFromBaidu~activity-2-121569398-blog-85287599.235^v29^pc_relevant_default_base3&utm_relevant_index=3#4_devtoolset_47)
    - [5. 查看gcc版本号：](https://huaweicloud.csdn.net/6356103fd3efff3090b596c1.html?spm=1001.2101.3001.6650.2&utm_medium=distribute.pc_relevant.none-task-blog-2~default~BlogCommendFromBaidu~activity-2-121569398-blog-85287599.235^v29^pc_relevant_default_base3&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2~default~BlogCommendFromBaidu~activity-2-121569398-blog-85287599.235^v29^pc_relevant_default_base3&utm_relevant_index=3#5_gcc_57)
    - [6. 一些issue:](https://huaweicloud.csdn.net/6356103fd3efff3090b596c1.html?spm=1001.2101.3001.6650.2&utm_medium=distribute.pc_relevant.none-task-blog-2~default~BlogCommendFromBaidu~activity-2-121569398-blog-85287599.235^v29^pc_relevant_default_base3&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2~default~BlogCommendFromBaidu~activity-2-121569398-blog-85287599.235^v29^pc_relevant_default_base3&utm_relevant_index=3#6_issue_68)



我们在**centos**下默认的**gcc**版本是**gcc4.8.5**，版本比较低，默认是支持编译**c++98**的，若在**C++\**程序中直接使用到\**c++11**的特性，则会报错。
**解决方案：** 在编译时加上`-std=c++11`即可，如`g++ test.cpp -o run -std=c++11`

在bash下直接下载 :

```brainfuck
yum install -y gcc gcc-c++
```

![在这里插入图片描述](E:\GitHub\GCC\images\1.png)
查看一下版本号：

```brainfuck
gcc --version
g++ --version
```

![在这里插入图片描述](E:\GitHub\GCC\images\2.png)

## 基本执行步骤：

### 1. 切换用户：

输入以下命令行切换到root用户，此时需要输入你对应的root密码

```ebnf
su - root
```

如下图所示：
![在这里插入图片描述](E:\GitHub\GCC\images\3.png)

### 2. 安装centos-release-scl：

```awk
sudo yum install -y http://mirror.centos.org/centos/7/extras/x86_64/Packages/centos-release-scl-rh-2-3.el7.centos.noarch.rpm
```

![在这里插入图片描述](E:\GitHub\GCC\images\4.png)

```awk
sudo yum install -y http://mirror.centos.org/centos/7/extras/x86_64/Packages/centos-release-scl-2-3.el7.centos.noarch.rpm
```

![在这里插入图片描述](E:\GitHub\GCC\images\5.png)

### 3. 安装devtoolset：

这里需要注意一下，如果想安装7.版本的，就改成`devtoolset-7-gcc`，以此类推

```apache
sudo yum install devtoolset-9-gcc-c++
```

![在这里插入图片描述](E:\GitHub\GCC\images\6.png)

### 4. 激活对应的devtoolset:

按理来说你可以一次安装多个版本的**devtoolset**，需要的时候用下面这条命令切换到对应的版本

```mipsasm
scl enable devtoolset-9 bash
```

**此条命令行也同样适用**

```gradle
source /opt/rh/devtoolset-9/enable
```

### 5. 查看gcc版本号：

```ada
gcc --version
```

![在这里插入图片描述](E:\GitHub\GCC\images\7.png)

```brainfuck
g++ --version
```

![在这里插入图片描述](E:\GitHub\GCC\images\8.png)

### 6. 一些issue:

**注意**：这条`scl enable devtoolset-9 bash`激活命令只对本次会话有效，重启会话或者切换用户后还是会变回原来的**4.8.5**版本，因为安装的`devtoolset`是在`/opt/rh`目录下的，如图所示：
![在这里插入图片描述](E:\GitHub\GCC\images\9.png)
每个版本的目录下面都有个**enable**文件：
![在这里插入图片描述](E:\GitHub\GCC\images\10.png)
如果需要启用某个版本，只需要执行命令行：

```bash
source ./enable
```

所以要想切换到某个版本，只需要执行：

```gradle
source /opt/rh/devtoolset-*/enable
```

可以将对应版本的切换命令写个**shell脚本**放在配置了环境变量的目录下，需要时随时切换，或者开机自启。**但是经过我自己的实践，不推荐上述方法。**

------

最直截了当的方法是**直接替换旧版本的gcc**

> 旧版本gcc运行的在`/usr/bin/gcc`，所以将该目录下的`gcc/g++`替换为安装的新版本gcc软连接，省去了每次都要enable，简洁明了

**依次执行以下命令：**

```awk
mv /usr/bin/gcc /usr/bin/gcc-4.8.5
ln -s /opt/rh/devtoolset-9/root/bin/gcc /usr/bin/gcc
```

现在就算是**永久性地启动指定版本的gcc**，这种方式适用于长期使用该版本进行编译，**切换bash依然有效**

切换到**Assassin**用户查看一下：

```coffeescript
[root@Ninghai ~]# su - Assassin
Last login: Fri Nov 26 22:20:43 CST 2021 from 182.118.236.53 on pts/1
[Assassin@Ninghai ~]$ g++ --version
g++ (GCC) 9.3.1 20200408 (Red Hat 9.3.1-2)
Copyright (C) 2019 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```

![在这里插入图片描述](E:\GitHub\GCC\images\11.png)
到这里就ok了~~