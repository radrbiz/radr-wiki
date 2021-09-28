---
title: Google身份验证器
chapter: 1
order: 4
layout: default.zh
lang: zh
---

* auto-gen TOC
{:toc}

# Google身份验证

支持动态口令的app包括微软验证器（Microsoft Authenticator）、 Google Authenticator等，可以通过应用商店进行下载。

雷达钱包账户系统现支持Google的动态口令。在手机端生成动态口令后，交易中除了用正常交易密码外，需要输入一次动态口令才能验证成功，消除账户遭到恶意攻击的潜在可能。

本文以Google Authenticator为例，介绍 Google Authenticator 的基本的安装和使用方法。

## 启用Google身份验证器

### 下载最新版Google身份验证器

![googleauthenticate](/assets/images/google_authenticate/googleauthenticate.jpg){:height="200px" width="200px"}

目前Google身份验证器支持iOS，Android和黑莓；
  1. iOS: 支持iphone，ipad，ipod touch；在AppStore搜索google authenticator 或直接点击 🌐 [这里](https://itunes.apple.com/cn/app/google-authenticator/id388497605)；
  2. Android：要在您的Android设备上使用Google身份验证器，您必须安装Android 2.1或更高版本。在各大安卓市场搜索google authenticator；
  3. 黑莓：在 BlackBerry 上打开网络浏览器。访问 m.google.com/authenticator。下载并安装该应用。

### 在RadrTrade启用Google身份验证器

  1. 在雷达交易页面 “设置”-“密码管理”-“动态密码”选项中，选择开启Google身份验证器
  2. 弹出的确认框中选择Google身份验证器
      
      ![confirm](/assets/images/google_authenticate/confirm.png){:height="300px" width="300px"}
  3. 点击确认，输入密码（如果当前开启了手机短信验证，还需要输入短信随机码）
  4. 密码验证通过后，页面会显示一个二维码
      
      ![barcode](/assets/images/google_authenticate/barcode.png){:height="200px" width="100px"}
  5. 打开手机上的Google身份验证器应用。如果第一次使用，选择设置-扫描二维码
      
      ![img_3346](/assets/images/google_authenticate/img_3346.png){:height="300px" width="300px"}
  6. 扫描二维码，成功后会在app里出现一个动态随机码
      
      ![img_3348](/assets/images/google_authenticate/img_3348.png){:height="300px" width="300px"}
  7. 在RadrTrade中，需要输入密码时，输入Google身份验证器中的动态密码进行验证。

### 在RadrTrade关闭Google身份验证器
  1. 在“设置”-“密码管理”-“动态密码”选项中，选择“关闭”
  2. 弹出的验证密码输入框中输入交易密码和Google身份验证器中的动态口令；
  3. 密码、口令验证通过，则Google身份验证器被关闭；
  4. 注：重新开启Google身份验证器不会将原有口令置为无效，需要选择“更改”或“找回”才能更换新的口令。

### 找回Google身份验证器
  如果你已经通过实名认证，可以提交反馈单进行重置。

## 注意事项!!!

*公式中C目前使用时间戳作为动态计数器，所以要求用户手机上的时间尽量与标准时间同步，否则会校验失败(大于2分钟会有非常大的几率失败）；*{: style="color: red"}.

## 原理说明

Google的两步验证算法源自另一种名为HMAC-Based One-Time Password的算法，简称HOTP。HOTP的工作原理如下：
  * 客户端和服务器事先协商好一个密钥K，用于一次性密码的生成过程，此密钥不被任何第三方所知道。此外，客户端和服务器各有一个计数器C，并且事先将计数值同步。
  * 进行验证时，客户端对密钥和计数器的组合(K,C)使用HMAC（Hash-based Message Authentication Code）算法计算一次性密码，公式如下：
    * HOTP(K,C) = Truncate(HMAC-SHA-1(K,C))
    * 上面采用了HMAC-SHA-1，当然也可以使用HMAC-MD5等。HMAC算法得出的值位数比较多，不方便用户输入，因此需要截断（Truncate）成为一组不太长十进制数（例如6位）。用户将这一组十进制数输入并且提交之后，服务器端同样的计算，并且与用户提交的数值比较，如果相同，则验证通过。如果不相同，则验证失败。
