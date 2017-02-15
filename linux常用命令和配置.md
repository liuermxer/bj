#linux常用命令和配置
## 创建用户
	简单模式:
		adduser 'username' "大部分默认"
	复杂模式:
		useradd [opt] 'username'
			[opt]:
				-c 指定一段注释性描述
				-d 指定用户目录
				-g 指定用户所属用户组
				-G 指定用户所属的附加组
				-s 指定用户的登陆Shell
				-u 指定用户的ID
		用户创建完毕后需要 passwd 'username' 创建用户密码
##普通用户添加管理员权限
	1) sudo su "切换到管理员权限"
	2) vi /etc/sudoers "必须是管理员权限打开"
	3) 在 root ALL=(ALL:ALL) ALL 下面添加用户
			username = (ALL:ALL) ALL
## 防火墙
### ufw
	启动/关闭/重启
		ufw enable[default deny]|disable|reload
	重置
		ufw reset
	开放/关闭端口
		ufw allow|delete allow 'port'
	查看状态
		ufw status
	允许某个IP允许访问所有端口
		ufw allow from 'IP'
	禁止外部访问 某个服务
		ufw deny '服务'
## 设置中文语言包
	Ubuntu:
		1) sudo apt-get install language-pack-zh-han* "下载中文语言包支持"
		2) sudo vim /etc/default/locale "打开语言包配置文件"
			更改为:
			LANG = "zh_CN.UTF-8"
			LANGUAGE = "zh_CH:zh"
		3) 重启服务器
	CentOS:
	