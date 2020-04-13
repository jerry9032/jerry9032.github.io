---
title: “App”已损坏，无法打开，您应该将它移到废纸篓
date: 2020-04-12 13:45:44
category: Mac
disqus: y
---

最近下载了一个 [Adobe Zii](https://www.adobezii.com/)，正要运行的时候报这么一个错：

![已损坏，无法打开](/images/mac-app-damaged-could-not-open-01.png)

## 原因

macOS 启用了安全机制，默认只信任 Mac App Store 下载的软件以及拥有开发者 ID 签名的软件，但是同时也阻止了没有开发者签名的 “老实软件”。

## 解决方案

macOS Mojave 10.14 及以下版本，只需将“允许任意来源”打开就行了。

```
$ sudo spctl --master-disable
```

但是！！在 macOS 10.15.x 系统对于未签名的应用又缩减了权限，光打开“允许任意来源”还是不够的，需要将 app 身上的一个扩展属性删掉：

```
$ sudo xattr -rd com.apple.quarantine /Applications/Adobe\ Zii\ 2020\ 5.1.9.app
```

## 深层次原因

那神秘的“com.apple.quarantine”这个 EA (extended attribute)到底是什么呢？

quarantine 这个词就是免疫、隔离类似的意思。苹果系统自 OSX 10.5 加入了一个叫 GateKeeper 保护机制，从互联网上下载来的文件，会被自动打上 com.apple.quarantine 标志，系统根据这个附加属性对这个文件作出限制。

macOS 10.14 即以下版本，安全限制还没这么严格，有这个属性的 app 需要确认才可执行，一旦被确认了，此属性就会被删掉。但 macOS 10.15 Catalina 对系统安全性大大的加强了，对于有这个 EA 的软件直接提示“已损坏”。

我们对下载的 dmg、dmg 内的 app 和拷贝到 /Applications 目录的三个文件分别观察：

```shell
# 这是下载的 dmg 文件，有 EA
$ xattr -p com.apple.quarantine ~/Downloads/Adobe\ Zii\ 5.1.9/Adobe\ Zii\ 5.1.9.dmg
0181;5e93e524;Chrome;FFE3A99D-9E02-4F2C-B8DD-2E0F2E07685F

# 这是 dmg 挂载后，dmg 内部的 app，无 EA
$ xattr -p com.apple.quarantine /Volumes/Adobe\ Zii\ 5.1.9/Adobe\ Zii\ 5.1.9.app
xattr: Adobe Zii 2020 5.1.9.app: No such xattr: com.apple.quarantine

# 这是将 app 拷贝到 /Applications 目录后，有 EA
$ xattr -p com.apple.quarantine /Applications/Adobe\ Zii\ 5.1.9.app
0181;5e93e524;Chrome;FFE3A99D-9E02-4F2C-B8DD-2E0F2E07685F
```

因此它整套流程是这样的：

1. Chrome 下载后，将整个 dmg 文件加上了“com.apple.quarantine” 这个 EA；
2. dmg 挂载后，无论将里面的什么文件拷贝出来，Finder 都会自动将 dmg 的所有 EA 附着到拷出来的文件上；
3. macOS 即可在用户打开文件时做出相应的操作。