# 介绍

**全网最好用的 V2Ray 一键安装脚本 &amp; 管理脚本**   

**小白也能轻松搭建自己的梯子、科学上网、魔法上网**

# 特点

- 自动化安装
- 零学习成本
- 支持所有主流协议
- 一键启用 BBR
- 一键更改伪装网站
- 一键变更 (端口/UUID/密码/域名/路径/加密方式/SNI/动态端口/等...)

# 脚本使用说明
## 安装准备
* 在执行脚本之前，先去租一个国外的vps服务器
   1. 推荐一下我自己用的[服务器厂商vultr](https://www.vultr.com/?ref=9594735)，特点是**免费更换ip，按需计费，部署简单，可以用支付宝结算**
* 先下载一个ssh客户端，方便与服务器进行交互，推荐用**MobaXterm**，特点是**占用内存小，轻便好用**

## 执行安装脚本(建议采用ubantu系统)   

`curl https://raw.githubusercontent.com/FelixLan/v2ray/master/install.sh | bash`   


* 安装成功，如图所示：  
![image](https://github.com/FelixLan/v2ray/assets/44452818/6e961bb5-e493-42dd-a55c-e20b7136addb)   

* 安装成功后，输出一系列服务端信息，先别急着配置客户端
  
* 先测试ip和端口是否能正常链接使用(测试入口：https://tcp.ping.pe/)
* 测试方法，直接输入ip:端口(示例：`77.22.11.22:8766`)，点击Go
   1. 如果显示sucessflu,则进行下一步   
   2. 如果显示failed,则先排查端口问题

**注意：一定要确保端口没问题，才能进行下一步**   
* 导致端口异常的原因一般是：
   1. 防火墙没关(解决方式：关闭服务器的防火墙)
   2. 端口被占用(解决方式：换个端口重新测试、或者杀掉占用端口的进程)

* 排查清楚了，这时候将最新的配置信息，直接复制vmess唯一链接，通过剪切板导入客户端，启用客户端，应该就能正常访问Google

**部署完成，就这么简单，愉快的冲浪吧**

>如果这时候仍无法正常使用v2ray访问Google，建议使用 `v2ray add ss` 命令添加一个 SS 看看能不能正常访问Google
   1. 如果能正常访问，证明服务端配置没有问题
   2. 则大概率是服务端与客户端的内核版本不兼容(解决方式：换其他客户端、或者降低服务端的内核版本：`v2ray update core 4.45.2`)
   3. **备注**:请尽量将客户端内核和服务器端内核保持一致！内核版本低于 5 可能会出现莫名其妙的问题


# 帮助

使用: `v2ray help`

```
V2Ray script v4.0 by 233boy
Usage: v2ray [options]... [args]...

基本:
   v, version                                      显示当前版本
   ip                                              返回当前主机的 IP
   get-port                                        返回一个可用的端口

一般:
   a, add [protocol] [args... | auto]              添加配置
   c, change [name] [option] [args... | auto]      更改配置
   d, del [name]                                   删除配置**
   i, info [name]                                  查看配置
   qr [name]                                       二维码信息
   url [name]                                      URL 信息
   log                                             查看日志
   logerr                                          查看错误日志

更改:
   dp, dynamicport [name] [start | auto] [end]     更改动态端口
   full [name] [...]                               更改多个参数
   id [name] [uuid | auto]                         更改 UUID
   host [name] [domain]                            更改域名
   port [name] [port | auto]                       更改端口
   path [name] [path | auto]                       更改路径
   passwd [name] [password | auto]                 更改密码
   type [name] [type | auto]                       更改伪装类型
   method [name] [method | auto]                   更改加密方式
   seed [name] [seed | auto]                       更改 mKCP seed
   new [name] [...]                                更改协议
   web [name] [domain]                             更改伪装网站

进阶:
   dd, ddel [name...]                              删除多个配置**
   fix [name]                                      修复一个配置
   fix-all                                         修复全部配置
   fix-caddyfile                                   修复 Caddyfile
   fix-config.json                                 修复 config.json

管理:
   un, uninstall                                   卸载
   u, update [core | sh | caddy] [ver]             更新
   U, update.sh                                    更新脚本
   s, status                                       运行状态
   start, stop, restart [caddy]                    启动, 停止, 重启
   t, test                                         测试运行
   reinstall                                       重装脚本

测试:
   client, genc [name]                             显示用于客户端 JSON, 仅供参考
   debug [name]                                    显示一些 debug 信息, 仅供参考
   gen [...]                                       同等于 add, 但只显示 JSON 内容, 不创建文件, 测试使用
   no-auto-tls [...]                               同等于 add, 但禁止自动配置 TLS, 可用于 *TLS 相关协议
   xapi [...]                                      同等于 v2ray api, 但 API 后端使用当前运行的 V2Ray 服务

其他:
   bbr                                             启用 BBR, 如果支持
   bin [...]                                       运行 V2Ray 命令, 例如: v2ray bin help
   api, convert, tls, run, uuid  [...]             兼容 V2Ray 命令
   h, help                                         显示此帮助界面

谨慎使用 del, ddel, 此选项会直接删除配置; 无需确认
反馈问题) https://github.com/233boy/v2ray/issues
文档(doc) https://233boy.com/v2ray/v2ray-script/
```
