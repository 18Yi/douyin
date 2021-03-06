# 抖音通信协议 2.9.1版本协议签名

## 简介

通过抖音通信协议实现自动化爬取抖音视频，批量注册登录，点赞，评论, 视频下载上传等功能

抖音通信协议支持抖音 iOS 2.9.1（最新）/iOS 2.8.0/2.7.0/2.0.0 版本协议，提供生成iOS设备信息功能，方便调用协议(其他版本协议请自测)

提供生成签名服务，方便对抖音通信协议进行签名。签名参数: `as`, `mas`, `ts`

因为2.7.0签名/2.8.0签名/2.9.1签名算法相同，所以可以调用API加签服务中的2.7.0的签名算法，使用对应版本的APPINFO信息即可。

项目持续更新中...


iOS协议手机抓包操作 参考: [在 iPhone 上利用 Charles 抓包](https://www.jianshu.com/p/8825179786ac)

## 禁止高并发请求访问公用服务器！！！
## 禁止高并发请求访问公用服务器！！！
## 禁止高并发请求访问公用服务器！！！
服务器配置入门级别，调用人数多，禁止单一IP并发量大，谢谢。否则加入自动封禁IP功能


## 使用说明
通过调用API加签服务来完成获取新的设备信息及协议签名。

实现过程:
1. 通过访问 `https://api.appsign.vip:2688/token/douyin/version/2.7.0` 获取抖音协议2.7.0的加签token，其他版本如2.6.0，修改version后面的版本号，如果不添加/version/<版本号>参数(暂不支持，有需要可以提issus)，默认版本号为最新版本，token有效期为60分钟
2. 如果没有设备信息可以请求 `https://api.appsign.vip:2688/douyin/device/new/version/2.7.0` 获取新的设备信息，包括install_id, vid, device_id, openudid 等， 设备信息为永久使用，版本号参考token获取中的版本号设置
3. 有了设备信息和加签Token， 需要通过参数构造加签字符串，调用 `https://api.appsign.vip:2688/sign` 完成参数的加签

---

> token有效期为一个小时，支持多线程进行加签，token失效之前无需重复获取
> 设备信息依据需要进行获取

## API参数
1. 获取抖音加签Token
```
https://api.appsign.vip:2688/token/douyin  # 默认版本为最新
https://api.appsign.vip:2688/token/douyin/version/2.7.0
```
```
{
    "token":"5826aa5b56614ea798ca42d767170e74
