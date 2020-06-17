---
id: auth
title: Auth 概念
---

# Auth

## AAA
* Authentication - 鉴权
* Authorization - 授权
* Accounting - 审计

# 验证授权

授权验证是一个很敏感的话题,在一个大型企业里往往需要一个专门的团队来负责,这里整理一些和授权验证相关的基本内容.

## 基础

不管是采用何种方式,都要首先保证链接安全,即至少是使用 HTTPS,为了简化开发和快速使用可使用 [letsencrypt](https://letsencrypt.org/) 提供的证书来提供安全链接.

出于安全考虑,也可以选择在客户端加密,即用户提交到服务器的的密码已经是加密过的,例如 sha1 用户的密码,这样也能避免用户密码的直接泄露.

## bcrypt
* 在线测试和生成工具 https://www.dailycred.com/article/bcrypt-calculator

## CAS
* [apereo/cas](https://github.com/apereo/cas) - Apereo CAS - Enterprise Single Sign On for all earthlings and beyond.

## ACL
https://loopback.io/doc/en/lb3/ACL-REST-API.html
http://docs.aws.amazon.com/zh_cn/AmazonS3/latest/dev/acl-using-rest-api.html


