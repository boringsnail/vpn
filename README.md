# vpn


首先连接到你的VPS，怎么连接就不用我说了吧，连接的时候注意下你自己的端口和密码即可，密码忘了就重新生成个。

以root用户运行以下命令，一行一行的粘贴进去即可：

```
yum -y install wget
wget --no-check-certificate http://blog.whsir.com/uploads/ss.sh
chmod +x ss.sh
./ss.sh 2>&1 | tee shadowsocks.log
```

运行后会提示下面内容，直接回车即可（如果没反应就再敲下回车），然后就开始等待了。
#############################################################
# One click Install Shadowsocks(Python)
# Intro: http://blog.whsir.com
#
# Author: whsir
#
#############################################################

Please input password for shadowsocks:
(Default password: whsir):
安装完成后显示内容如下：

Congratulations, ss install completed!
Your Server IP:your_server_ip
Your Server Port:443
Your Password:your_password
Your Local IP:127.0.0.1
Your Local Port:1080
Your Encryption Method:aes-256-cfb

Welcome to visit:blog.whsir.com
Enjoy it!

卸载方法：

./ss.sh uninstall

多端口多密码配置：

#vi /etc/shadowsocks.json

按i粘贴以下配置（原有内容需要删除）
```
{
"server":"0.0.0.0",
"local_address":"127.0.0.1",
"local_port":1080,
"port_password":{
"7788":"password0",
"7789":"password1",
"7790":"password2"
},
"timeout":300,
"method":"aes-256-cfb",
"fast_open": false
}
```
7788、7789、7790为你要设置的端口号，后面是每个端口号对应的密码，设置端口号的时候不要有冲突端口就好。

timeout：超时时长，这里默认300。

注意：如果新添加端口和密码，格式要和给出的示例保持一致，最后一个端口和密码后面没有逗号

最后要记得重启下shadowsocks

需要用到的命令：
启动：service shadowsocks start
停止：service shadowsocks stop
重启：service shadowsocks restart
状态：service shadowsocks status

 

最近有大量朋友反映，在Centos6上安装会报错

报错内容如下：

Installed /usr/lib/python2.6/site-packages/setuptools-33.1.1-py2.6.egg
Processing dependencies for setuptools==33.1.1
Finished processing dependencies for setuptools==33.1.1
Searching for pip
Reading http://pypi.python.org/simple/pip/
Couldn't find index page for 'pip' (maybe misspelled?)
Scanning index of all packages (this may take a while)
Reading http://pypi.python.org/simple/
No local packages or download links found for pip
error: Could not find suitable distribution for Requirement.parse('pip')

pip install failed! Please visit blog.whsir.com and contact.

解决办法：

yum -y install http://dl.fedoraproject.org/pub/epel/6/x86_64/Packages/p/python-pip-7.1.0-1.el6.noarch.rpm

然后在执行

./ss.sh 2>&1 | tee shadowsocks.log
