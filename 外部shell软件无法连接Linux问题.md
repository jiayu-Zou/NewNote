**问题：**

发现下载好的Ubuntu、Centos虚拟机无法通过Xshell连接。

**原因：**

虚拟机 ssh 没有启动。

在Linux终端执行命令：

```shell
ps -e | grep ssh
```

如果没有显示 sshd 字样，说明确实 ssh 没有启动。（此时一般显示 ssh-agent 字样）

**解决：**

```shell
# 1.安装openssh-server
# 未安装时，使用后续命令会报错：Failed to start sshd.service: Unit sshd.service not found.
sudo apt install openssh-server

# 2.启动服务，两条指令任选其一
sudo /etc/init.d/ssh start

sudo service sshd start

# 3.安装成功后默认就会启动服务。
```

（2022.04.17，Ubuntu-20.04.4 完成上述后连接成功）

如果 ssh 已启动，还是无法连接，那么需要查看 ssh 的配置文件。

```shell
# 打开 sshd_config
vim /etc/ssh/sshd_config

# 找到 PermitRootLogin prohibit-password
# 将 prohibit-password 改为 yes

# 重启ssh-server
sudo /etc/init.d/ssh restart
```

