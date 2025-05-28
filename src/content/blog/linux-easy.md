---
title: "Linux 命令备忘录"
description: "简单的linux命令，适合不常用linux但学过的快速回忆"
pubDate: "05 20 2025"
image: /image/linux/kk.png
categories:
  - tech
tags:
  - Linux
badge: BE
---

linux命令通用格式 command [-options] [parameter]。

## 基础命令

**ls [-a -l -h] [linux路径]**\
-a all\
-l 竖向展示\
-h 查看文件大小

**cd [linux路径]**\
若当前目录为/home/root\
cd desktop = cd /home/root/desktop =cd ~/desktop =cd ./desktop\
cd ..到上一级 cd ../.. 上两级 以此类推

**pwd 输出当前工作目录**

**mkdir [-p] [linux路径]**\
创建文件夹\
-p 自动创建不存在的父目录

**touch [linux路径]**\
创建文件

**cat [linux路径]**\
查看文件内容

**more [linux路径]**\
可翻页的cat，空格翻页，q退出

**cp [-r] 参数1(源)，参数2**\
-r 递归复制文件夹

**mv 参数1 参数2**\
移动文件\文件夹，改名

**rm [-r -f] 参数1 参数2 ...参数N**\
-f 强制删除\
-r 递归删除\
支持通配符\*，模糊匹配

**which 要查找的命令**\
查找命令的本地文件在哪

**find 起始路径 -name "被查找的文件名"**\
支持通配符\*，模糊匹配\
find 起始路径 -size +|-n[KMG]\
+-表示大于或小于\
例：find / -size -10k

**grep [-n] 关键字 文件路径**\
从文件中通过关键字过滤文件行\
-n 显示匹配的行的行号\
关键字中带有空格则需""包裹\
文件路径可用管道符输入

**wc [-c -m -l -w] 文件路径**\
-c 统计bytes数量\
-m 统计字符数量\
-l 统计行数\
-w 统计单词数量\
文件路径可用管道符输入

**echo "输出的内容"**\
用反引号``来将其作为命令而非字符输出

**tail [-f -num] linux路径**\
查看文件尾部内容\
-f 持续跟踪（日志）\
-num 看几行默认10

**vi/vim 文件路径**\
输入模式 i a o进入 esc退出
i当前光标进入 a 之后 o 下一行 pgup向上翻页 /搜索模式 n向下搜索 N向上搜索
dd删除当前行 ndd 删n行，yy复制，nyy，p粘贴，u撤销，ctrl r反向撤销修改
gg跳到首行，G尾行
底线模式 ：进入 wq保存退出

**su [-] [用户名]**\

- 在切换用户后加载环境变量\
  切换用户后 exit回退上一个用户\
  sudo 其他命令\
  临时获取root权限

  ## 解压缩

**tar [-c -v -x -f -z -C] 参数1 参数2。。。参数n**\
-c 创建压缩文件，用于压缩模式\
-x 解压模式\
-v 显示压缩，解压过程，用于查看进度\
-f 要创建的文件或者要解压的文件，必须在所有选项最后面\
-z gzip模式，不使用-z就是普通tarball格式，必须在最前\
-C 选择压缩的目的地，必须单独使用\
tar则-cvf 解压-xvf \
tar.gz则-zcvf 解压-zxvf

**zip [-r] 参数1 参数n**\
-r 被压缩包含文件夹时

**unzip [-d] 参数**\
-d 指定解压位置，同-C

## 系统命令

**yum [-y] [install | remove | search] 软件名称**\
-y，自动确认，无需手动确认安装或卸载

**systemctl start | stop | status | enable | disable 服务名**\
启动 | 关闭 | 查看状态 | 开启开机自启 | 关闭开机自启

**ln -s 参数1 参数2**\
-s 创建软连接\
参数1：被链接的文件或文件夹\
参数2：目的地

**date [-d] [+格式化字符串]**\
-d 按照给定的字符串显示日期 “+1 day”\
格式化字符串：%Y年 %y年份后两位 %m月 %d日 %H小时 %M分钟 %S秒 %s从70年到现在的秒数

**hostname set-hostname 主机名**\
修改主机名

**ping [-c num] ip或主机名**\
-c 检查次数 无则无限次

**wget [-b] url**\
非交互的文件下载器\
-b 后台下载，将日志写入工作目录的wget-log文件

**curl [-O] url**\
-O 用于下载文件，当url是下载链接时，用此选项保存文件

**nmap 被查看的ip地址**\
查看ip地址的端口占用情况

**netstat -anp | gerp 端口号**\
查看指定端口的占用情况

**ps [-e -f]**\
-e 显示出全部的进程\
-f 展示全部信息

**kill [-9] 进程ID**\
-9 表示强制关闭

**top**\
查看进程的cpu，内存的使用情况\
-p 只显示某个进程\
-d 设置刷新时间\
-c 显示产生进程的完整命令\
-n 指定刷新次数\
-i 不显示任何闲置或无用的进程信息\
-u 查找特定用户启动的进程

**df [-h]**\
查看硬盘使用情况\
-h 以更加人性化的单位显示

**iosat [-x] [num1] [num2]**\
cpu 磁盘的相关信息\
-x 显示更多信息\
num1 数字刷新间隔 num2 刷新次数

**sar -n DEV num1 num2**\
查看网络的相关统计\
-n 查看网络，DEV表示查看网络接口

**export 变量名=变量值**\
临时设置一个环境变量\
source /etc/profile 所有用户永久生效\
source ~/bashrc 当前用户永久生效

**rs**\
上传\
**sz 要下载的文件**

## 符号

**管道符 |**\
将左边的结果作为右边的输入\
cat test.txt | gerp itheima

**重定向符**\
">将左侧命令的结果，覆盖写入右边"\
">>追加写入"

**\$符号**\
用于取变量的值\
取得环境变量的值就可以通过语法：\$环境变量名

## 快捷键

ctrl+C，强制停止\
ctrl+D，退出账户或退出某些特定程序（python）的专属页面\
history，历史输入命令\
！+命令前缀，自动执行上一次匹配前缀的命令（近期）\
ctrl+l ，清屏终端（clear命令）\
ctrl+r，输入内容匹配历史命令\
ctrl +键盘左右/a/e，左右跳一个单词/开头结尾

## 用户权限相关

**visudo root配置用户sudo权限**

**groupadd 用户组名**\
创建用户组\
**groupdel用户组名**\
删除用户组

**useradd [-g -d] 用户名**\
-g 指定用户的组，不指定则创建同名组加入\
-d 指定home路径，不指定则/home/用户名

**userdel [-r] 用户名**\
-r 同时删除用户home目录

**id [用户名]**\
查看所属组

**usermod -aG 用户组 用户名**\
将指定加入指定组

**getent passwd**\
查看当前系统中那些用户（7份信息）\
**getent group**\
用户组

**(d-l)rwxr-xr-x**\
d文件夹，-文件，l软链接\
r读，w写，x执行\
本用户权限，本组权限，其他用户权限

**chmod [-R] 权限 文件或文件夹**\
-R 对文件夹内的全部内容应用同样的操作\
例：chmod -R u=rwx,g=rx,o=x hello.txt\
r4 w2 x1 则简写为chmod -R 751 hello.txt

**chown [-R] [用户][:][用户组] 文件或文件夹**\
-R 同上\
：用于分割用户与用户组
