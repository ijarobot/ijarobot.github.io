---
layout: post
title: "iOS使用NSUserDefaults的小细节问题"
date: 2014-02-25 13:45
comments: true
categories: ios,objective-c,cocoa
---
【摘要 以下的问题其实与NSUserDefaults是没有太大的关系。与O-c的id类型有关，因为[userDefaults objectForKey:@"xxx"]返回的是id类型。 以下的代码跑起来大多数情况是正常的，但有时候会崩溃】



#######逻辑：从NSUserDefaults中读出userList

如果userList中没有这个email则将当前email添加userList，然后保存userList到UserDefaults
代码如下：

```objc
    NSMutableArray *userList = [userDefaults objectForKey:@"userList"];
    if(userList){
        if(![userList containsObject:self.email]){
            [userList addObject:self.email];
        }
    }else{
        userList = [NSMutableArray array];
        [userList addObject:self.email];
    }
    [userDefaults setObject:userList forKey:@"userList"];
    [userDefaults synchronize];
```

以上的问题其实与NSUserDefaults是没有太大的关系。与O-c的id类型有关，因为[userDefaults objectForKey:@"xxx"]返回的是id类型。

上面的代码跑起来大多数情况是正常的，出错的概率虽然比较小，但有时候会崩溃，错误信息如下

    2014-02-25 13:14:15.503 SAY[3725:70b] *** Terminating app due to uncaught exception 'NSInternalInconsistencyException', reason: '-[__NSCFArray insertObject:atIndex:]: mutating method sent to immutable object'

错误出在这一行代码

    [userList addObject:self.email];

此时userList实际上是NSArray的实例，虽然它被显示的声明为NSMutableArray*.

安全的写法为

    NSMutableArray *userList = [NSMutableArray arrayWithArray:[userDefaults objectForKey:@"userList"]];