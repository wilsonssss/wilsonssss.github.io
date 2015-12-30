---
layout: post
title:  "搭建android sdk mirror "
date:   2014-07-20 16:19:18 +0800
categories: wilson update
---

`server端:`

+ 1.脚本:https://github.com/opencas/mirrors/blob/master/script/bin/android.py 放到服务器(注意定期检查作者是否update脚本)
+ 2.修改脚本中的out_dir为sdk仓库的绝对路径
     如out_dir = '/home/vagrant/android/sdk_mirror/android/repository'
+ 3.开启http服务, 指向/home/vagrant/android/sdk_mirror/
+ 4.设置定时任务(每天的23点50分进行更新)   
	50 23 * * * /usr/bin/python /home/vagrant/android/sdk_mirror/android/repository/android_fetch.py > /home/vagrant/android/sdk_mirror/android/repository/update_check.txt

`client端:`  

+ 1.运行$AndroidSDK/tools/android
+ 2.菜单栏 - 设置
  * http proxy server:192.168.199.21（sdk mirror的http host）  
  * http proxy port:8182（sdk mirror的http 端口）  
  * "Use download cache" 打钩, "Clear Cache"  
  * Force https:// to http:// 打钩’
+ 3.菜单栏 - packages - reload  
<img src="../imgs/sdk_mirror.png" width="300" align="center"/>   
