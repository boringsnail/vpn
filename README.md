# vpn


# 安装
以root用户运行以下命令，一行一行的粘贴进去即可：

```
wget --no-check-certificate -O shadowsocks-all.sh https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocks-all.sh
chmod +x shadowsocks-all.sh
./shadowsocks-all.sh 2>&1 | tee shadowsocks-all.log
```

修改配置
`vi /etc/shadowsocks-python/config.json`

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

# 常用命令
start 启动 stop 停止 restart 重启 status 状态

Shadowsocks-libev 版：
```
/etc/init.d/shadowsocks-libev start
/etc/init.d/shadowsocks-libev stop
/etc/init.d/shadowsocks-libev restart
/etc/init.d/shadowsocks-libev status
```
Shadowsocks-Python 版：
```
/etc/init.d/shadowsocks-python start
/etc/init.d/shadowsocks-python stop
/etc/init.d/shadowsocks-python restart
/etc/init.d/shadowsocks-python status
```
ShadowsocksR 版：
```
/etc/init.d/shadowsocks-r start
/etc/init.d/shadowsocks-r stop
/etc/init.d/shadowsocks-r restart
/etc/init.d/shadowsocks-r status
```
Shadowsocks-Go 版：
```
/etc/init.d/shadowsocks-go start
/etc/init.d/shadowsocks-go stop
/etc/init.d/shadowsocks-go restart
/etc/init.d/shadowsocks-go status
```
如何卸载
运行如下命令，根据提示，选择对应版本卸载
`./shadowsocks-all.sh uninstall`

# BBR加速

使用root用户登录，运行以下命令：
`wget --no-check-certificate https://github.com/teddysun/across/raw/master/bbr.sh && chmod +x bbr.sh && ./bbr.sh`
安装完成后，脚本会提示需要重启 VPS，输入 y 并回车后重启。



# shawdrock 下载
链接: https://pan.baidu.com/s/1KWeYTlpUZ5Y50hmFTRXnLQ 提取码: 58i8 
--来自百度网盘超级会员v5的分享
