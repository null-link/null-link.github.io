---
layout: article 
title: Checksum Quick Reference
tags: checksum filehash crypto sha md5 sha512 sha256 sha1 openssl shasum
aside:
  toc: true
license: false
show_subscribe: false
show_author_profile: true
---

Using the shasum utility on macOS to calculate the sha512 hash of a file on macOS

`shasum -a 512 <filename>`

Using OpenSSL to calculate the sha512 hash using binary input

`openssl dgst -sha512 -binary <filename> | openssl base64 -A`

Example:

```zsh
openssl dgst -sha512 -binary draw.io-13.9.9.dmg | openssl base64 -A
```
