---
layout: post
title: "Android 聊天控件Android-Chat-Widget"
date: 2014-12-06 12:14
comments: true
categories: Android,聊天控件,Chat,Android-Chat-Widget
---

【摘要 我在开发[`SAY`](/blog/2014/11/07/say-project/)这个项目时，基于Xmpp做了IM模块。前几天整理[`SAY`](/blog/2014/11/07/say-project/)项目的代码封装了这样一个聊天的控件】

Android-Chat-Widget
===================

An Android Chat Widget, like WhatsApp \ Line \ WeChat

Android-Chat-Widget 像微信、WhatsApp、Line一样的聊天控件。



Demo
===================
![](http://ww2.sinaimg.cn/mw690/d3a067e3gw1en2optdql3j20ae0ib0to.jpg)
<!--more-->

![](https://code.csdn.net/java2eer/android-chat-widget/blob/master/Android-Chat-Widget-Example/chatdemo.gif)



How to use?
===================
1.In Layout

```xml

     <com.jialin.chat.MessageInputToolBox
        android:id="@+id/messageInputToolBox"
        android:layout_width="match_parent"
        android:layout_height="wrap_content" 
      />
```

2.In Activity
```java
    	/**
    	 * init MessageInputToolBox
    	 */
    	private void initMessageInputToolBox() {
    		box = (MessageInputToolBox) findViewById(R.id.messageInputToolBox);
    
    		box.setOnOperationListener(new OnOperationListener() {
    
    			@Override
    			public void send(String content) {
    				// TODO
    			}
    
    			@Override
    			public void selectedFace(String content) {
    				// TODO
    			}
    
    			@Override
    			public void selectedFuncation(int index) {
    				// TODO
    			}
    
    		});
    
    		box.setFaceData(faceData);
    
    		box.setFunctionData(functionData);
    	}
```

source reposiotry
===================
Github:[https://github.com/ijarobot/Android-Chat-Widget](https://github.com/ijarobot/Android-Chat-Widget)

Git@OSC:[http://git.oschina.net/ijarobot/Android-Chat-Widget](http://git.oschina.net/ijarobot/Android-Chat-Widget)