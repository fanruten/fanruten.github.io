---
layout: post
title: "Билд без codesign"
date: 2014-06-26 00:58:41 +0400
comments: true
categories: [xCode, codesign]
---

{% img center http://fanruten.github.io/images/2014-06-26-build-without-codesign/1.png 600 %}

Если попытаться собрать приложение с такой конфигурацией, то будет ошбика:
```
CodeSign error: code signing is required for product type 'Application'  
```
Чтобы xCode собирал билды без подписи, надо открыть один из следующих файлов в зависимости от Deployment Target:
```
/Applications/Xcode.app/Contents/Developer/Platforms/iPhoneOS.platform/Developer/SDKs/iPhoneOS7.1.sdk/SDKSettings.plist  
/Applications/Xcode.app/Contents/Developer/Platforms/iPhoneSimulator.platform/Developer/SDKs/iPhoneSimulator6.1.sdk/SDKSettings.plist  
/Applications/Xcode.app/Contents/Developer/Platforms/iPhoneSimulator.platform/Developer/SDKs/iPhoneSimulator7.0.sdk/SDKSettings.plist  
/Applications/Xcode.app/Contents/Developer/Platforms/iPhoneSimulator.platform/Developer/SDKs/iPhoneSimulator7.1.sdk/SDKSettings.plist  
```
И поставить ключ CODE_SIGNING_REQUIRED в NO.

{% img center http://fanruten.github.io/images/2014-06-26-build-without-codesign/2.png %}

Теперь можно собрать бинарник для которого команда "codesign --display --verbose=4 SomeApp" выведет:
```
SomeApp: code object is not signed at all  
```

