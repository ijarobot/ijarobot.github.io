---
layout: post
title: "SAY Project"
date: 2014-11-07 12:20
comments: true
categories: say,project,app
---

##Introduce

于13年年末离开磨房网，至今差不多一年左右的时间。与香港的4位朋友在做`SAY`这个APP，香港负责需求、任务安排、测试以及后期的运营推广，我在深圳负责开发所有的功能、发布上线。


经过我们5人共同的努力，现在Android已经发布2.1版，iOS已经发布2.0版。目前还没有多少真正的用户，都是认识的朋友在帮忙试用。计划再迭代几个版本后，再由香港团队负责推广。


`SAY`-- Something Around You的首写字母的缩写，主要的功能是找共同兴趣爱好的人发起活动、参加活动、记录活动过程中美好的时刻，以及活动开始前后的沟通与交流。另外，商家用户也可以发布收费的商业活动。


##Architecture
<img src='/images/say/screenshoot/say-architecture.jpg' style="max-height: 800px; max-width: 800px;">


##Technology
**Server:**`Java` `Xmpp` `Spring` `Mybatis` `Duboo` `Rop` `Maven` `Tigase`

**DB:**`MySQL`

**云平台:**`AWS新加坡节点`  `EC2(两个实例)`  `RDS(两个mysql实例)`  `S3(文件存储主要是保存图片)`  `SES(用来发送邮件)`  `SNS(Android、iOS远程消息推送)`

**iOS:**`XMPPFramework` `ViewDeck` `SDWebImage` `Facebook-SDK` `AWS-SDK` 

**Android:**`ASmack`  `Android-PullToRefresh`  `Universal-Image-Loader` `Facebook-SDK` `AWS-SDK` [`Android-Chat-Widget`](https://github.com/ijarobot/Android-Chat-Widget)


##Screenshot

<table border="0" >
	<tr>
		<td><img src='/images/say/screenshoot/device-2014-12-11-120541.png' style="max-height: 565px; max-width: 1043px;"></td>
		<td width="50">  </td>
		<td><img src='/images/say/screenshoot/device-2014-11-19-153500.png' style="max-height: 565px; max-width: 1043px;"></td>
	</tr>
	<tr height="50"></tr>
	<tr>
		<td><img src='/images/say/screenshoot/device-2014-11-19-153543.png' style="max-height: 565px; max-width: 1043px;"></td>
		<td width="50">  </td>
		<td><img src='/images/say/screenshoot/device-2014-11-19-153655.png' style="max-height: 565px; max-width: 1043px;"></td>
	</tr>
	<tr height="50"></tr>
	<tr>
		<td><img src='/images/say/screenshoot/device-2014-12-11-120807.jpg' style="max-height: 565px; max-width: 1043px;"></td>
		<td width="50">  </td>
		<td><img src='/images/say/screenshoot/device-2014-11-19-152341.jpg' style="max-height: 565px; max-width: 1043px;"></td>
	</tr>
	<tr height="50"></tr>
	<tr>
		<td><img src='/images/say/screenshoot/device-2014-11-19-153432.jpg' style="max-height: 565px; max-width: 1043px;"></td>
		<td width="50">  </td>
		<td><img src='/images/say/screenshoot/device-2014-11-19-153445.png' style="max-height: 565px; max-width: 1043px;"></td>
	</tr>
	<tr height="50"></tr>		
</table>


##Dowloads

<table border="0" >
	<tr>
		<td style="text-align: center;"><b>Android</b></td>
		<td width="85">  </td>
		<td style="text-align: center;"><b>iOS</b></td>
	</tr>
	<tr height="10" ></tr>
	
	<tr>
		<td><a href="https://play.google.com/store/apps/details?id=com.say">
	  			<img alt="Get it on AWS" src="/images/say/screenshoot/say-android.png" />
			</a>
		</td>
		<td width="85">  </td>
		<td><a href="https://itunes.apple.com/us/app/say/id914290055?l=zh&ls=1&mt=8">
	  			<img alt="Get it on App Store" src="/images/say/screenshoot/say-ios.png" />
			</a>
		</td>
	</tr>

	
	<tr>
		<td style="text-align: center;"><a href="https://play.google.com/store/apps/details?id=com.say">
	  			<img style="vertical-align:middle;" src="/images/say/screenshoot/en_generic_rgb_wo_60.png" />
			</a>
		</td>
		<td width="85">  </td>
		<td style="text-align: center;"> <a href="https://itunes.apple.com/us/app/say/id914290055?l=zh&ls=1&mt=8">
	  			<img style="vertical-align:middle;" src="/images/say/screenshoot/badge_appstore-lrg_60.png" />
			</a>
		</td>
	</tr>	
</table>






