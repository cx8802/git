## 开启ssh服务

1、  首先，要确保CentOS7安装了  openssh-server，在终端中输入  yum list installed | grep openssh-server

此处显示已经安装了  openssh-server，如果又没任何输出显示表示没有安装  openssh-server，通过输入  yum install openssh-server

开启ssh服务需要root权限，先用root账户登陆

先检查有没有安装ssh服务：rpm -qa | grep ssh

![https://img-blog.csdn.net/20180708040857622?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2JhaWJhaWdhbw==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70](E:%5CTypora_note%5Cimage%5Cclip_image001.png)

如果没有安装ssh服务就安装 ： yum install openssh-server

安装好后在ssh配置文件里进行配置 : vim /etc/ssh/sshd_config

![https://img-blog.csdn.net/20180708041128310?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2JhaWJhaWdhbw==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70](E:%5CTypora_note%5Cimage%5Cclip_image002.png)

![https://img-blog.csdn.net/20180708041439304?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2JhaWJhaWdhbw==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70](E:%5CTypora_note%5Cimage%5Cclip_image003.png)

![https://img-blog.csdn.net/20180708041431137?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2JhaWJhaWdhbw==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70](E:%5CTypora_note%5Cimage%5Cclip_image004-1589349825196.png)

用esc+：wq 保存退出

![https://img-blog.csdn.net/20180708041446243?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2JhaWJhaWdhbw==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70](E:%5CTypora_note%5Cimage%5Cclip_image005.png)

修改完后用 /bin/systemctl start sshd.service 开启ssh服务,这个命令没有回显

![https://img-blog.csdn.net/20180708041744843?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2JhaWJhaWdhbw==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70](E:%5CTypora_note%5Cimage%5Cclip_image006-1589349825196.png)

开启后用 ps -e | grep sshd 检查一下ssh服务是否开启

![https://img-blog.csdn.net/20180708041858646?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2JhaWJhaWdhbw==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70](E:%5CTypora_note%5Cimage%5Cclip_image007.png)

再用netstat -an | grep 22检查一下22端口是否开启

将ssh服务添加到自启动列表中：systemctl enable sshd.service
