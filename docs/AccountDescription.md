# 账号互通说明
## 需求：
因部分渠道需求，需要在Android和ios实现账号互通
## 解决方案
### **ios的uid返回**
ios平台quick的返回uid的规则是根据quick的渠道code来加前缀。   
(code如下或请参考图片\img\ChannelCode.png)建议核对
--|code|渠道名称
--|---|---
1|525|麦游
3|692|C游
4|738|btgameIOS(乐嗨嗨海外)
11|1031|九妖
12|1034|3733(悦游)
14|1401|巨乐玩
15|1293|简易玩_iOS
### **Android的uid返回**
我们会在Android返回的Uid前加quick返回的Code作为渠道的标识   
(例如下图为3733的账号返回)   
![如果不能显示，请在\img\AndroidReturnUid.png找到图片](\img\AndroidReturnUid.png "code")
### **互通**
请贵方在登录验证的时候做判断,如果为同一渠道请做账号互通处理.   
目前有上述渠道有互通需求
另外__**特别的注意的是，请加上账号顶掉机制**__，   
以防同一渠道同一账户同时登录ios和Android   
### **返回例子**
------------------------------------------------
>A渠道Code：123
>
>A渠道账号adb   
>quick安卓返回userid:abc123     
>quickios返回userid:abc123     
>
>鸿游安卓返回userid:123_abc123   
>-- ----------------------------------------------
>A渠道Code：123
>
>A渠道账号:acdb   
>quick安卓返回userid:abc1234   
>quickios返回userid:abc1234   
>
>鸿游安卓返回userid:123_abc1234
------------------------------------------------
>B渠道Code：234
>
>B渠道账号:acdb   
>quick安卓返回userid:abc123   
>quickios返回userid:abc123
>
>鸿游安卓返回    234_abc123
------------------------------------------------
其中需要注意的是AB两个渠道都出现了abc123的userid故拼接渠道Code消除歧义