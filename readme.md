

# GitHub实现的注册机数据库

1. 注册机,授权用户列表
2. 软件更新,软件更新列表以及下载
3. 收款信息的获取

产生日期 9/13/2017 11:53:21 PM 

## 工作流程:

客户端请求验证,收到[MSG];注册机生成字符串,并加密得到[MSG],保存此项目上

客户端:

	通过网络请求userID.html页面,获得json字符串
	[{appid:'XXX',state:0}]  已经经过加密过的
	base64解密,公钥解密,json解析

注册机:

	生成 [{appid:'XXX',state:0}] 私钥加密,的字符串,base64编码,提交到服务器.

## 访问接口

LICENSE_ROOT = https://sangxiaokai.github.io/app_licenser

1.授权用户数据库

	Users
	  -----demo@demo.html
	  -----user@user.html
比如Url: [LICENSE_ROOT]/Users/demo@demo.html


数据:
	[{appid:'XXX',state:0}] ----加密后的字符串


2.软件更新接口已经下载列表

	Apps
	  -----[app_name]
			------update.html
					json[{version:'xxx',file:'download/XXX.exe',info:'the infomation',force:true}]
			------downloads/
					------ app.exe
	  -----[app_name]

	[{version:'版本号',file:'下载文件',info:'更新信息',force:是否强制更新}]

比如Url: [LICENSE_ROOT]/[APP_NAME]/update.html

3.付款信息
	Apps
	  -----[app_name]
			------pay/ 付款说明链接静态文档
				------index.html 付款说明
					------img/alipay.jpg 支付宝二维码
					------img/weixin.jpg 微信二维码










