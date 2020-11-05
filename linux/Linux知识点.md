# Linux知识点

### 磁盘分区

正常实体机大概使用 /dev/sd[a-]的磁盘文件名

#### 磁盘的组成

磁盘的组成主要有磁盘盘，机械手臂，磁盘读取头，和主轴马达

**磁盘盘**上又分成 **扇区**和**磁道**两种单位。

**扇区**物理设计有两种大小  分别是 **512bytes** 与**4Kbytes**

### 目录树结构

最重要的是根目录“/”

所有文件都是由根目录衍生来的。

### 文件系统

挂载：挂载就是利用一个目录当进入点，将磁盘分区槽放置在该目录下。

### 基本命令

[linux命令大全](https://www.runoob.com/linux/linux-command-manual.html)

### linux的文件权限与目录配置

#### linux文件属性

su - 切换root身份之后，ls-al可查看文件权限

r读权限 4 

w写权限 2

x执行权限 1

chgrp：改变文件所属群组权限

chown:改变文件拥有者权限

chmod：改变文件的权限。

chmod 777 filename

第一个7是rwx对应owner

第二个7是rwx对应group

第三个7是rwx对应other

#### linux目录配置

![linux1.png](..\img\linux1.png)

- `/`：根目录，一般根目录下只存放目录，在Linux下有且只有一个根目录。所有的东西都是从这里开始。当你在终端里输入“/home”，你其实是在告诉电脑，先从/（根目录）开始，再进入到home目录。
- `/bin`: /usr/bin: 可执行二进制文件的目录，如常用的命令ls、tar、mv、cat等。
- `/boot`：放置linux系统启动时用到的一些文件，如Linux的内核文件：/boot/vmlinuz，系统引导管理器：/boot/grub。
- `/dev`：存放linux系统下的设备文件，访问该目录下某个文件，相当于访问某个设备，常用的是挂载光驱 mount /dev/cdrom /mnt。
- `/etc`：系统配置文件存放的目录，不建议在此目录下存放可执行文件，重要的配置文件有 /etc/inittab、/etc/fstab、/etc/init.d、/etc/X11、/etc/sysconfig、/etc/xinetd.d。
- `/home`：系统默认的用户家目录，新增用户账号时，用户的家目录都存放在此目录下，~表示当前用户的家目录，~edu 表示用户 edu 的家目录。
- `/lib`: /usr/lib: /usr/local/lib：系统使用的函数库的目录，程序在执行过程中，需要调用一些额外的参数时需要函数库的协助。
- `/lost+fount`：系统异常产生错误时，会将一些遗失的片段放置于此目录下。
- `/mnt`: /media：光盘默认挂载点，通常光盘挂载于 /mnt/cdrom 下，也不一定，可以选择任意位置进行挂载。
- `/opt`：给主机额外安装软件所摆放的目录。
- `/proc`：此目录的数据都在内存中，如系统核心，外部设备，网络状态，由于数据都存放于内存中，所以不占用磁盘空间，比较重要的目录有 /proc/cpuinfo、/proc/interrupts、/proc/dma、/proc/ioports、/proc/net/* 等。
- `/root`：系统管理员root的家目录。
- `/sbin`: /usr/sbin: /usr/local/sbin：放置系统管理员使用的可执行命令，如fdisk、shutdown、mount 等。与 /bin 不同的是，这几个目录是给系统管理员 root使用的命令，一般用户只能"查看"而不能设置和使用。
- `/tmp`：一般用户或正在执行的程序临时存放文件的目录，任何人都可以访问，重要数据不可放置在此目录下。
- `/srv`：服务启动之后需要访问的数据目录，如 www 服务需要访问的网页数据存放在 /srv/www 内。
- `/usr`：应用程序存放目录，/usr/bin 存放应用程序，/usr/share 存放共享数据，/usr/lib 存放不能直接运行的，却是许多程序运行所必需的一些函数库文件。/usr/local: 存放软件升级包。/usr/share/doc: 系统说明文件存放目录。/usr/share/man: 程序说明文件存放目录。
- `/var`：放置系统执行过程中经常变化的文件，如随时更改的日志文件 /var/log，/var/log/message：所有的登录文件存放目录，/var/spool/mail：邮件存放的目录，/var/run:程序或服务启动后，其PID存放在该目录下。

### vim编辑器

三种模式：

正常模式：可以使用快捷键

插入模式/编辑模式：输入i之后才能进入编辑模式

命令行模式：读取，存盘，替换，离开vim

![img](..\img\linux2.png)

esc 然后冒号  q退出不保存，wq退出并保存   :q!不保存

快捷键：

![img](..\img\linux3.png)

### **用户管理**

#### 添加用户

useradd [选项] 用户名

cd表示 change directory 切换目录

当用户创建成功后，会自动创建家目录，也可以通过useradd -d 指定目录

给用户设置密码

passwd xm

#### 删除用户

userdel xm

#### 删除用户及家目录的用户目录

userdel -r xm

#### 查询用户信息

id xm      查看xm的用户信息

id root   查看root用户信息

su xm

权限高的用户切换权限低的用户不需要输入密码

#### **用户组**

#### **把用户添加到组**

groupadd 组名

groupdel 组名  删除组名

#### 增加用户直接加上租

useradd -g 用户组 用户名

#### 修改用户的组

usermod -g 用户组 用户名

**/etc/passwd 文件**

用户（user）的配置文件，记录各种信息

每行的意义：  用户名：口令：用户标识号：注释行描述：主目录：登录shell

/etc/shadow

口令的配置文件

/etc/group

组的配置文件

### **压缩和解压类** 	

gzip/gunzip指令

gzip用于压缩文件，gunzip 用于解压的。

gzip（只能将文件压缩为 *.gz）

gunzip 文件.gz

zip/unzip指令

zip     将文件压缩为zip

unzip    解压zip文件

zip

-r:递归压缩，

unzip	-d：指定压缩后的文件存放目录

tar指令

打包指令，最后打包成 .tar.gz文件

tar[选项] xxx.tar.gz（打包目录，压缩后的文件格式.tar.gz）

### **RPM和YUM**

查看已安装的rpm列表    rpm -qa|grep xx

rpm -qf  文件的全路径名，查询文件所属的软件包

rpm -e RPM  卸载rpm

安装rpm包  rpm -ivh RPM包的全路径

-i  安装install

-v提示 verbose

-h进度条 hash

yum

yum是一个shell前端软件包管理器，基于rpm包管理，能够自动下载rpm并且安装，可以自动处理依赖性关系

yum list|grep xx 软件列表

安装yum包   yum install xxx