---
title: git で ssl クライアント証明書を利用する
date: 2015-03-04 11:13 JST
tags:
---

はい

```
git init
openssl pkcs12 -in mycert.p12 -nocerts -out mycert.key -nodes
openssl pkcs12 -in mycert.p12 -clcerts -nokeys -out mycert.crt
openssl pkcs12 -in mycert.p12 -cacerts -nokeys -out cacert.crt
git config --local http.sslCert "/mycert.crt"
git config --local http.sslKey "/mycert.key"
git config --local http.sslCaInfo "/cacert.crt"
# 証明書を追加するので無効化しない
# git config --local http.sslVerify "false"
git pull git pull 
```

まあこんなことするより ssh で繋ぐほうが楽。ssl で繋いだ。

参考
-----

[](http://www.wakoond.hu/2013/07/using-git-with-https-client-certificate.html)

