## Linux Commands You Should Know

* cd（切换目录）

```	相对路径		cd  .		cd  ..		cd  ~		cd -		cd  ../		cd ~/foo_bar		绝对路径		以/开头```

* 列出文件

```	ls	ls -l	ll
```

* alias

```		alias	alias peiqi='echo XiaoZhuPeiQi'	unalias ```
系统中默认的alias```	[root@dplinux network-scripts]# alias 	alias cp='cp -i'	alias l.='ls -d .* --color=auto'	alias ll='ls -l --color=auto'	alias ls='ls --color=auto'	alias mv='mv -i'	alias peiqi='echo Wu Sir'	alias rm='rm -i'	alias which='alias | /usr/bin/which --tty-only --read-alias --show-dot --show-tilde'	[root@dplinux network-scripts]# ```

* 常用热键

```	ctrl + c	ctrl + d	ctrl+l # 清屏	ctrl+a # 回行首	ctrl+e # 回行尾		ctrl+k # 清除光标之后	ctrl+u # 清除光标之前```	

* 文件查看操作

    * cat	    * less # 按屏显示文件内容

    ```    	快捷键	   上下左右方向键	   G     # 文尾	   gg    # 文首	   空格  # 翻屏	   q     # 退出文件查看    ```
    * more # 类似less查看文件内容的命令    * head

    ```    	head 文件    	head -n 行数 文件    	head -行数 文件    ```
    * tail

    ``` 
    参数选项同head    -f    ```
    
## 系统开关机类
  * shutdown -h now `# 关闭系统(1)` 
  * shutdown -h hours:minutes & 按预定时间关闭系统 
  * shutdown -c 取消按预定时间关闭系统 
  * shutdown -r now 重启(1) 
  * init 0 关闭系统(2) 
  * telinit 0 关闭系统(3) 
  * reboot 重启(2) 
  * logout 注销   

## 文件和目录管理类 
### 变换当前目录(change directory)
  * cd /home 进入 '/ home' 目录' 
  * cd .. 返回上一级目录 
  * cd ../.. 返回上两级目录 
  * cd 进入个人的主目录 
  * cd ~user1 进入个人的主目录 
  * cd - 返回上次所在的目录 
  * pwd 显示工作路径  

### 查看目录中的文件(list files)  
  * ls 查看目录中的文件 
  * ls -F 查看目录中的文件 
  * ls -l 显示文件和目录的详细资料 
  * ls -a 显示隐藏文件 
  * ls *[0-9]* 显示包含数字的文件名和目录名 
  * tree 显示文件和目录由根目录开始的树形结构(1) 
  * lstree 显示文件和目录由根目录开始的树形结构(2)   

### 创建目录
  * mkdir dir1 创建一个叫做 'dir1' 的目录' 
  * mkdir dir1 dir2 同时创建两个目录 
  * mkdir -p /tmp/dir1/dir2 创建一个目录树   

### 删除文件/目录
  * rm -f file1 删除一个叫做 'file1' 的文件' 
  * rmdir dir1 删除一个叫做 'dir1' 的目录' 
  * rm -rf dir1 删除一个叫做 'dir1' 的目录并同时删除其内容 
  * rm -rf dir1 dir2 同时删除两个目录及它们的内容     

### 新建文件&查看文件
  * touch  test.txt    新建一个叫text.txt 的文件(后缀txt可以不写)
  * more test.txt     查看文件内容同(不能编辑)
  * vi  test.txt  编辑文件，编辑中有很多vi的命令

### 复制和移动文件
  * mv dir1 new_dir 重命名/移动 一个目录 
  * cp file1 file2 复制一个文件 
  * cp dir/* . 复制一个目录下的所有文件到当前工作目录 
  * cp -a /tmp/dir1 . 复制一个目录到当前工作目录 
  * cp -a dir1 dir2 复制一个目录     

## 文件搜索
  * find / -name file1 从 '/' 开始进入根文件系统搜索文件和目录 
  * find / -user user1 搜索属于用户 'user1' 的文件和目录 
  * find /home/user1 -name \*.bin 在目录 '/ home/user1' 中搜索带有'.bin' 结尾的文件 
  * find /usr/bin -type f -atime +100 搜索在过去100天内未被使用过的执行文件 
  * find /usr/bin -type f -mtime -10 搜索在10天内被创建或者修改过的文件 
  * find / -name \*.rpm -exec chmod 755 '{}' \; 搜索以 '.rpm' 结尾的文件并定义其权限 
  * find / -xdev -name \*.rpm 搜索以 '.rpm' 结尾的文件，忽略光驱、捷盘等可移动设备 

## 用户管理类 
  * groupadd group_name 创建一个新用户组 
  * groupdel group_name 删除一个用户组 
  * groupmod -n new_group_name old_group_name 重命名一个用户组 
  * useradd -c "Name Surname " -g admin -d /home/user1 -s /bin/bash user1 创建一个属于 "admin" 用户组的用户 
  * useradd user1 创建一个新用户 
  * userdel -r user1 删除一个用户 ( '-r' 排除主目录) 
  * usermod -c "User FTP" -g system -d /ftp/user1 -s /bin/nologin user1 修改用户属性 
  * passwd 修改口令 
  * passwd user1 修改一个用户的口令 (只允许root执行) 
  
## 文件权限管理类
  * 使用 "+" 设置权限，使用 "-" 用于取消
  * ls -lh 显示权限 
  * ls /tmp | pr -T5 -W$COLUMNS 将终端划分成5栏显示 
  * chmod ugo+rwx directory1 设置目录的所有人(u)、群组(g)以及其他人(o)以读（r ）、写(w)和执行(x)的权限 
  * chmod go-rwx directory1 删除群组(g)与其他人(o)对目录的读写执行权限 
  * chown user1 file1 改变一个文件的所有人属性 
  * chown -R user1 directory1 改变一个目录的所有人属性并同时改变改目录下所有文件的属性 
  * chown user1:group1 file1 改变一个文件的所有人和群组属性 
  * chmod u+s /bin/file1 设置一个二进制文件的 SUID 位 - 运行该文件的用户也被赋予和所有者同样的权限 
  * chmod u-s /bin/file1 禁用一个二进制文件的 SUID位 
  * chmod g+s /home/public 设置一个目录的SGID 位 - 类似SUID ，不过这是针对目录的 
  * chmod g-s /home/public 禁用一个目录的 SGID 位 
  * chmod o+t /home/public 设置一个文件的 STIKY 位 - 只允许合法所有人删除文件 
  * chmod o-t /home/public 禁用一个目录的 STIKY 位   

  文件的特殊属性
  
  * 文件的特殊属性 - 使用 "+" 设置权限，使用 "-" 用于取消 
  * chattr +a file1 只允许以追加方式读写文件 
  * chattr +c file1 允许这个文件能被内核自动压缩/解压 
  * chattr +d file1 在进行文件系统备份时，dump程序将忽略这个文件 
  * chattr +i file1 设置成不可变的文件，不能被删除、修改、重命名或者链接 
  * chattr +s file1 允许一个文件被安全地删除 
  * chattr +S file1 一旦应用程序对这个文件执行了写操作，使系统立刻把修改的结果写到磁盘 
  * chattr +u file1 若文件被删除，系统会允许你在以后恢复这个被删除的文件 
  * lsattr 显示特殊的属性 

## 打包和压缩
  * zip
  * gzip
  * tar

## 进程管理
* ps
* kill
* killall
* pkill

## 网络调试
* curl
* HTTP Code
* wget

## 软件安装
* rpm
* yum(依赖)
* 源码安装


## 系统状态查看/管理相关命令

* 状态查看
   * w
   * top
   * iftop
   * iotop
   * htop
   * free
       * cache/buffer
       * 读cache 写buffer
* 进程管理    
   * ps
       * ps -ef
       * ps aux
   * kill(下节课讲解)
* 网络管理
   * ping
   * telnet
   * nmap
   * ip
       * ip a
       * ip ro sh
   * ifconfig
   * netstat
   * ss
* 磁盘管理
   * df
   * du
   * fdisk/parted 

