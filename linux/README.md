# Linux 驱动分发指南

## 目录结构

- master分支下总是最新的驱动文件,原则上与版本号最大的tag所包含的文件相同,请优先将master分支下的驱动分发给用户.
- tags下面是按照驱动的版本号整理的驱动文件,如果特定用户需要特定版本的驱动,请切换为特定版本后下载,分发给用户.
- rpm 目录中,包含使用RPM/YUM包管理架构的Linux发行版所使用的驱动文件的预编译RPM包, SRPM包(非预编译包). 目前预编译包分为两大类: CentOS/RHEL; SUSE(sles).
- deb 目录中,包含使用DPKG/APT包管理架构的Linux发行版所使用的驱动文件的预编译DEB包. 目前预编译包分为两大类: Debian; Ubuntu.
- 所有预编译包均包括:
	1. 驱动模块包(shannon-module).
	2. 实用工具包(shannon-utils).
- 分发预编译包时请同时分发这两个包. 请注意:所有RPM包管理架构平台共享一个utils包,在rpm目录获取; 所有DPKG包管理架构每个发行版的utils包都不相同,需要在各个发行版目录获取.
- src 目录中,包含驱动文件的源代码tar包.
- 分发SRPM包时,需要一同分发utils包;分发源代码tar包时,只需要源码包一个包.

## 驱动分发原则(分发流程)

1. 确定操作系统发行版  
    执行命令:
    ```
    cat /etc/issue
    ```
    输出示例:
    ```
    rikki@debian:~$ cat /etc/issue
    Debian GNU/Linux 7 \n \l
    ```
	- CentOS,RHEL(RedHat Enterprise Linux),  发行版请使用rpm/CentOS 目录中对应的系统版本目录中的驱动module文件, 为RPM包.
	- SUSE(SUSE Linux Enterprise,openSUSE)(sles)发行版请直接使用rpm/SUSE目录中对应的系统版本目录中的驱动module文件, 为RPM包.
	- OL(Oracle Linux), Fedora 发行版请直接使用rpm/SRPM目录中的SRPM包.
	- Debian, Unbuntu 发行版, 请使用deb 目录中的对应操作系统及版本下的驱动文件, 为DEB包. 如本例中应该使用deb/Debian/7/ 目录下的相关驱动文件包.
	- 其他Linux发行版, 请使用src 目录中的驱动文件源代码,配合[用户手册](#user_manual)指导用户自己编译安装驱动, 文件为tar包.
    
2. 确定操作系统kernel版本号.  
    执行命令:
    ```
    uname -a
    ```
    输出示例:
    ```
    rikki@debian:~$ uname -a
    Linux debian 3.2.0-4-amd64 #1 SMP Debian 3.2.57-3+deb7u1 x86_64 GNU/Linux
    ```
	- 选择对应的kernel版本所对应的驱动,文件按照包, 在本例中 使用的是Debian 操作系统, 对应的kernel版本号为 3.2.0-4-amd64, 所以应该选择deb/Debian/7/shannon-module-3.2.0-4-amd64_2.7.6_amd64.deb 及 deb/Debian/7/shannon-utils_2.7.6_amd64.deb 这两个文件(这是一个示例,请不要原教旨).
	- 在rpm目录中没有找到对应发行版的对应kernel版本的驱动包,请使用SRPM包:rpm/SRPM/ 里面的SRPM包.
	- 如果按照上述规则没有找到对应的文件,请使用src目录中的源代码tar包,配合[用户手册](#user_manual)指导用户编译安装驱动,或联系FAE Team成员取得支持.
	
## <a name="user_manual"></a>用户手册
最新用户手册地址:
[http://gitlab.eggpain.us:8000/doc/manual/blob/master/Driver_and_Util/UG201_Direct-IO_PCIe_SSD_用户手册_user_manual.pdf](http://gitlab.eggpain.us:8000/doc/manual/blob/master/Driver_and_Util/UG201_Direct-IO_PCIe_SSD_用户手册_user_manual.pdf)
