# Those-years-of-Python
爬虫、Django、软件破解工具、逆向破解、数据挖掘等等
第一次写github，不足之处请大佬多多指教
           鞋名：孙小兜
个人网址：www.sunxiaodou.icu

一、	Python SMTP发送邮件

介绍一下smtplib模块
1、用smtplib库来实现邮件发
python的smtplib提供了一种很方便的途径发送电子邮件。它对smtp协议进行了简单的封装。
import smtplib
smtpObj = smtplib.SMTP( [host [, port [, local_hostname]]] )
———————————————————————————————————————
host: SMTP 服务器主机。 你可以指定主机的ip地址或者域名如: runoob.com，这个是可选参数。
port: 如果你提供了 host 参数, 你需要指定 SMTP 服务使用的端口号，一般情况下 SMTP 端口号为25。
local_hostname: 如果 SMTP 在你的本机上，你只需要指定服务器地址为 localhost 即可。

************************************************************************************************
实例、
#!/usr/bin/python
# -*- coding: UTF-8 -*-
import smtplib
from email.mime.text import MIMEText
from email.utils import formataddr 
my_sender='**********@qq.com'    # 发件人邮箱账号
my_pass = 'xxxxxxxxxx'              # 发件人邮箱密码
my_user='**********@qq.com'      # 收件人邮箱账号，我这边发送给自己
def mail():
    ret=True
    try:
        msg=MIMEText('填写邮件内容','plain','utf-8')
        msg['From']=formataddr(["FromRunoob",my_sender])  # 括号里的对应发件人邮箱昵称、发件人邮箱账号
        msg['To']=formataddr(["FK",my_user])              # 括号里的对应收件人邮箱昵称、收件人邮箱账号
        msg['Subject']="QQ发送邮件测试"                # 邮件的主题，也可以说是标题
 
        server=smtplib.SMTP_SSL("smtp.qq.com", 465)  # 发件人邮箱中的SMTP服务器，端口是25
        server.login(my_sender, my_pass)  # 括号中对应的是发件人邮箱账号、邮箱密码
        server.sendmail(my_sender,[my_user,],msg.as_string())  # 括号中对应的是发件人邮箱账号、收件人邮箱账号、发送邮件
        server.quit()  # 关闭连接
    except Exception:  # 如果 try 中的语句没有执行，则会执行下面的 ret=False
        ret=False
    return ret
ret=mail()
if ret:
    print("邮件发送成功")
else:
    print("邮件发送失败")
************************************************************************************************

2、
schedule 模块可以非常方便地实现：周期性地在每天的某个时间点上执行任务。
分
schedule.every(10).minutes.do(job)
小时
schedule.every().hour.do(job)
天
schedule.every().day.at("10:30").do(job)
周
schedule.every().monday.do(job)
点
schedule.every().wednesday.at("13:15").do(job)

3、
MIMEText 类来实现支持HTML格式的邮件，支持所有HTML格式的元素，包括表格，图片，动画，css样式，表单等。

4、用requests爬取网址 http://www.weather.com.cn/weather/101280601.shtml 的天气预报信息，爬出下来的天气状况和温度文本，再调用邮件发送模块来实现定时发送。

5、
邮箱授权码的获取方式
1、登录电脑版QQ邮箱，选择最上方的“设置”。
2、切换到账户详情页面。
3、在账户页面往下拉，可以看到pop3设置，选择“开启”。
4、按照弹出的窗口提示操作进行密保验证。有多种方式可以验证，比如手机令牌等。推荐使用短信验证。
5、按照短信验证的提示发送短信。发送成功后直接点击“我已发送”。


