

![](http://img3.imgtn.bdimg.com/it/u=1587293988,596106613&fm=214&gp=0.jpg)

1. 关闭虚拟机，以 CentOS 为例
2. 设置第二块网卡，使用 host-only 模式，所有选项选择允许
3. 进虚拟机 ip -4 address，可以看到 192.168... 开头的ip
4. 虚拟机之间通许使用 192.168... ip
5. 如果还是不行，则执行 sudo iptables -F 清一下防火墙
