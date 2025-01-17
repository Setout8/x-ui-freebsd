# x-ui for FreeBSD

支持多协议多用户的 xray 面板, 本版本支持FreeBSD非root安装。

# 功能介绍

- 系统状态监控
- 支持多用户多协议，网页可视化操作
- 支持的协议：vmess、vless、trojan、shadowsocks、dokodemo-door、socks、http
- 支持配置更多传输配置
- 流量统计，限制流量，限制到期时间
- 可自定义 xray 配置模板
- 支持 https 访问面板（自备域名 + ssl 证书）
- 更多高级配置项，详见面板
  
# 安装须注意
1. 在安装前，请先准备好用户名，密码和两个端口（面板访问端口和流量监控端口）！
2. 如果你的服务器 cpu 架构不是 `amd64`，自行将命令中的 `amd64`替换为其他架构
```
cd ~
rm -rf ./x-ui
tar zxvf x-ui-freebsd-amd64.tar.gz
chmod +x x-ui/x-ui x-ui/bin/xray-freebsd-* x-ui/x-ui.sh
cp x-ui/x-ui.sh ./x-ui.sh
cd x-ui
crontab -l > x-ui.cron
echo "0 0 * * * cd $cur_dir/x-ui && cat /dev/null > x-ui.log" >> x-ui.cron
echo "@reboot cd $cur_dir/x-ui && nohup ./x-ui run > ./x-ui.log 2>&1 &" >> x-ui.cron
crontab x-ui.cron
rm x-ui.cron
nohup ./x-ui run > ./x-ui.log 2>&1 &
```

# 安装&升级（如这方式安装失败，请用下面上传的方式）
```
wget -O x-ui.sh -N --no-check-certificate https://raw.githubusercontent.com/Setout8/x-ui-freebsd/main/x-ui.sh && chmod +x x-ui.sh && ./x-ui.sh
```
# 上传到VPS根目录安装（以serv00为例）
1. 下载`x-ui.sh`文件到本地，文件名保持不变
2. 将`x-ui.sh`文件上传至VPS根目录，如：登陆`VPS面板`→图标`File manager`→根目录`My Files`
3. SSH登陆VPS,输入`chmod +x x-ui.sh`获得权限，再输入`./x-ui.sh`运行脚本，接着按提示操作即可

## 手动安装&升级

1. 首先从 https://github.com/Setout8/x-ui-freebsd/releases 下载最新的压缩包，一般选择 `amd64`架构
2. 然后将这个压缩包上传到服务器的 `/home/[username]`目录下，

## SSL证书申请

建议使用Cloudflare 15年证书

## Tg机器人使用（开发中，暂不可使用）

此功能未经测试！

## 建议系统

- FreeBSD 14+

# 特别感谢
[parentalclash](https://github.com/parentalclash/x-ui-freebsd)、[vaxilu](https://github.com/vaxilu/x-ui)
