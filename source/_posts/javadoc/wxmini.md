---
title: 微信小程序接口封装
date: 2025-06-26 16:49:06
index_img: /img/images.jpg
categories:
- Java文档
tags:
- 微信小程序
---

#### 初始化对象
  
```java
/**
 * 初始化对象
 * @param appid 小程序appID
 * @param secret 小程序秘钥
 */
WxMiniUtils wxMiniUtils = new WxMiniUtils(String appid,String secret);
```

#### 获取微信小程序token令牌
  
```java
/**
 * 获取微信小程序token令牌
 */
String getMiniToken()
```

#### 获取微信小程序用户的openID
  
```java
/**
 * 获取微信小程序用户的openID
 * @param js_code 小程序端获取的一次性code
 */
String getMiniOpenId(String js_code)
```

#### 获取微信小程序设备订阅码
  
```java
 /**
 * 获取微信小程序设备订阅码
 * @param token token
 * @param sn 设备编号
 * @param modelId  设备ID
 * @return 订阅码 5分钟有效期
 */
String getSnTicket(String token,String sn,String modelId)
```

#### 微信小程序推送信息
  
```java
 /**
 * 微信小程序推送信息
 * @param token token
 * @param openId 微信openId
 * @param page 点击跳转页面路径
 * @param templateId 模板ID
 * @param data 数据  key-value
 * @param env_version 跳转版本 release正式版（默认） developer开发版 trial体验版
 */
String sendTemplate(String token,String openId,String page,String templateId,Map<String,String> data,String env_version);
```

##### 微信小程序推送信息-开发版
  
```java
 /**
 * 微信小程序推送信息-开发版
 * @param token token
 * @param openId 微信openId
 * @param page 点击跳转页面路径
 * @param templateId 模板ID
 * @param data 数据  key-value
 */
String sendDevTemplate(String token,String openId,String page,String templateId,Map<String,String> data)
```

##### 微信小程序推送信息-体验版
  
```java
 /**
 * 微信小程序推送信息-体验版
 * @param token token
 * @param openId 微信openId
 * @param page 点击跳转页面路径
 * @param templateId 模板ID
 * @param data 数据  key-value
 */
String sendTrialTemplate(String token,String openId,String page,String templateId,Map<String,String> data)
```

##### 微信小程序推送信息-正式版
  
```java
 /**
 * 微信小程序推送信息-正式版
 * @param token token
 * @param openId 微信openId
 * @param page 点击跳转页面路径
 * @param templateId 模板ID
 * @param data 数据  key-value
 */
String sendTemplate(String token,String openId,String page,String templateId,Map<String,String> data)
```

#### 获取微信小程序手机号
  
```java
 /**
 * 获取微信小程序手机号
 * @param token token
 * @param code 小程序中获取的code
 * @return 手机号
 */
String getMiniPhone(String token,String code)
```

#### 小程序生成带参二维码
  
```java
 /**
 * 小程序生成带参二维码  生成后二维码链接为  page?scene=param
 * @param param 参数 a=1
 * @param page 页面 pages/index/index
 * @param env_version 发行版本 release正式版（默认） develop开发版 trial体验版
 */
String getUnlimitedQRCode(String token,String param,String page,String env_version)
```

##### 小程序生成带参二维码-正式版
  
```java
 /**
 * 小程序生成带参二维码  生成后二维码链接为  page?scene=param
 * @param param 参数 a=1
 * @param page 页面 pages/index/index
 */
String getUnlimitedQRCode(String token,String param,String page)
```

##### 小程序生成带参二维码-开发版
  
```java
 /**
 * 小程序生成带参二维码  生成后二维码链接为  page?scene=param
 * @param param 参数 a=1
 * @param page 页面 pages/index/index
 */
String getDevUnlimitedQRCode(String token,String param,String page)
```

##### 小程序生成带参二维码-体验版
  
```java
 /**
 * 小程序生成带参二维码  生成后二维码链接为  page?scene=param
 * @param param 参数 a=1
 * @param page 页面 pages/index/index
 */
String getTrialUnlimitedQRCode(String token,String param,String page)
```