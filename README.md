# wxbotwxidmes
PC微信机器人之实战分析通过wxid获取用户信息，微信二次开发SDK，微信开发API接口协议。非微信ipad协议、非mac协议,非安卓协议，api可实现微信99%功能； 无需扫码登录、可收发朋友圈、 查看朋友圈、朋友圈互动点赞、评论、 好友列表、微信消息收发、发文本消息、图片消息、名片消息、动图表情、发文件、删好友 添加好友、微信转账接收、分享小程序、分享名片、加通讯录好友、微信收藏等！ 清理僵尸粉、消息群发、通过好友请求、 微信建群、微信拉人进群、踢群成员、邀请群成员、退群、改群名称、群列表、发布群公告、多群消息同步等，wxbot,企业微信SDK,企业微信hook，个人微信开发sdk,微信机器人开发api,微信api接口，企业微信外部群机器人，企业微信机器人api，企业微信api，企业微信sdk接口，企业微信SDK、企业微信开发API，企业微信第三方开发接口适用于企业微信营销软件研发，企业微信工作手机研发，企业微信云控系统研发，企业微信客服系统研发，企业微信营销系统研发，企业微信客微商营销工具研发，企业微信scrm客服系统研发，企业微信聊天机器人，企业微信群管理机器人研发，企业微信协议API接口开发

本节主要分析通过wxid获取微信用户信息call，实现的思路是，首先附加微信到CE，在微信文件助手窗口，用CE搜索filehepler ，然后在PC微信切换到另外一个人的聊天窗口，看CE上面微信id变化，获得到当前人的微信id，在CE再次过滤，最后找到切换聊天窗口时，CE上面的微信id也一直变化，把这些移到下面，
![image](https://user-images.githubusercontent.com/96330669/172513726-57763268-5c6b-4051-82b4-6e27b9693b09.png)
然后把微信id和昵称记录下来，再找个用户的微信id和昵称记录下来，
最后筛选出4个地址，然后比较笨的办法是一个一个在OD里面试，也有一个技巧，一般连着的地址不是的，所以选择第一个，跟其他三个不连续的，去OD里面下一个内存访问断点。
![image](https://user-images.githubusercontent.com/96330669/172513744-2e50621a-3821-4c07-9e23-79b3dba538aa.png)
![image](https://user-images.githubusercontent.com/96330669/172513761-8d6fa4d1-5db9-47f0-adae-47a324acc85d.png)
然后在微信随便点击某个人的微信，看到OD断下来了，之后删除内存断点，然后在堆栈里面找，
然后找到一个从函数的开头，设置一个断点，然后在微信点击某个人的信息，看到是可以断下来了，然后跟踪断点，调试一下，
![image](https://user-images.githubusercontent.com/96330669/172513788-8997b777-c634-44ab-a523-4a8975415f11.png)
跟着断点走，找到疑似获取个人信息的函数，备注下来，同时下个断点，然后再点击某个人一个微信，看到这个断点断下来了，然后看下edi里面装的什么东西，发送是个缓冲区，看下这个缓冲区的大小是3DC，![image](https://user-images.githubusercontent.com/96330669/172513811-2652e313-84e3-4db0-964e-7eafcd12fbcb.png)
找到缓冲区和wxid，一个是可以接收他数据的，另外一个是你获取那一个微信的信息。然后把没用的信息nop掉从新运行一次，如果不崩溃，就不需要传这些参数，
![image](https://user-images.githubusercontent.com/96330669/172513826-8f36b070-7b43-4bb2-b7bb-eb11faa3bf56.png)
通过调试得到三个call，然后把偏移计算一下，复制call的地址，减去模块的地址，得到偏移地址。
![image](https://user-images.githubusercontent.com/96330669/172513847-601fd649-d087-4ac2-a687-dac43646ef41.png)

个微

目前已经实现了很多有趣的功能，运行稳定，比如：发各种消息，
接收各种消息，群管，下载文件，加好友，检测僵尸粉，朋友圈等等功能，
可提供接口，方便各种语言二次开发，欢迎技术交流，Q：2645542961
，请勿用于商业用途。
![image](https://user-images.githubusercontent.com/96330669/172514263-393485ff-3141-4751-920b-36352c52c595.png)

企业微信：
目前已经实现了大部分功能，运行稳定，比如：发各种消息，
接收各种消息，外部群内部群管理，下载文件，加好友等等功能，
可提供接口，方便各种语言二次开发，欢迎技术交流。


