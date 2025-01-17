【知识】linux防火墙及端口

# 查看对外开放的端口

```shell
# 查询开启的端口
netstat -ntulp | grep 端口号

# 查询防火墙开启的端口
firewall-cmd --query-port=666/tcp
```

# 查看防火墙状态

```shell
# 查看防火墙状态 
systemctl status firewalld
# 开启防火墙 
systemctl start firewalld  
# 关闭防火墙 
systemctl stop firewalld
# 开启防火墙 
service firewalld start 
# 若遇到无法开启
# 先用：
systemctl unmask firewalld.service 
# 然后：
systemctl start firewalld.service
```

# 对外开发端口

```shell
# 查看想开的端口是否已开：
firewall-cmd --query-port=6379/tcp
# 添加指定需要开放的端口：
firewall-cmd --add-port=123/tcp --permanent
# 重载入添加的端口：
firewall-cmd --reload
# 查询指定端口是否开启成功：
firewall-cmd --query-port=123/tcp

# 查看已经开放的端口：
firewall-cmd --list-ports

# 移除指定端口：
firewall-cmd --permanent --remove-port=123/tcp
```

