---
title: base64和七牛云上传下载应用笔记
summary: 使用Python对文件进行加密解密以及使用七牛SDK上传文件和获取私有文件下载URL
date: "2015-12-10T23:49:37Z"
tags: ["Python", "base64", "技术"]
categories: ["Python"]
reading_time: true  # Show estimated reading time?
share: false  # Show social sharing links?
profile: true  # Show author profile?
comments: false  # Show comments?
---
## base64加解密
Python3中使用base64加密解密数据一定要注意将数据转化成字节码，代码如下：
``` python
import base64
data = 'write what you want to write'
bytesString = data.encode(encoding="utf-8")
print(bytesString)
#base64 编码
encodestr = base64.b64encode(bytesString)
print(encodestr)
print(encodestr.decode())
#解码
decodestr = base64.b64decode(encodestr)
print(decodestr.decode())
```
## 七牛云存储
### 上传文件
首先七牛云账户中获取到 Access Key 和 Secret Key，然后再通过下面的代码进行文件上传：
``` python
# -*- coding: utf-8 -*-
access_key = '...'
secret_key = '...'
bucket_name = '...'
q = Auth(access_key, secret_key)
# 直接上传二进制流
key = 'a\\b\\c"你好'
data = 'hello bubby!'
token = q.upload_token(bucket_name)
ret, info = put_data(token, key, data)
print(info)
assert ret['key'] == key
key = ''
data = 'hello bubby!'
token = q.upload_token(bucket_name, key)
ret, info = put_data(token, key, data, mime_type="application/octet-stream", check_crc=True)
print(info)
assert ret['key'] == key
# 上传本地文件
localfile = __file__
key = 'test_file'
mime_type = "text/plain"
params = {'x:a': 'a'}
token = q.upload_token(bucket_name, key)
ret, info = put_file(token, key, localfile, mime_type=mime_type, check_crc=True)
print(info)
assert ret['key'] == key
assert ret['hash'] == etag(localfile)
```
### 私有文件下载
如果某个 bucket 是私有的，那么这个 bucket 中的所有文件只能通过一个的临时有效的 downloadUrl 访问：`http://<domain>/<key>?e=<deadline>&token=<dntoken>`
其中 dntoken 是由业务服务器签发的一个临时下载授权凭证，deadline 是 dntoken 的有效期。dntoken 不需要单独生成，SDK提供了生成完整 private_url 的方法（包含了 dntoken），示例代码如下：
``` python
# -*- coding: utf-8 -*-
# flake8: noqa
import requests
from qiniu import Auth
access_key = '...'
secret_key = '...'
q = Auth(access_key, secret_key)
bucket_domain = '...' #可以在空间设置的域名设置中找到
key = 'test_private_key' #key 就是上传到七牛空间中的文件名称
base_url = 'http://%s/%s' % (bucket_domain, key)
private_url = q.private_download_url(base_url, expires=3600)
print(private_url)
r = requests.get(private_url)
assert r.status_code == 200
```
生成 private_url 后，服务端下发 private_url 给客户端。客户端收到 private_url 后，和公有资源类似，直接用任意的 HTTP 客户端就可以下载该资源了。唯一需要注意的是，在 private_url 失效却还没有完成下载时，需要重新向服务器申请授权。
