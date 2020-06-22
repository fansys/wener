---
id: rook
title: Rook
---

# Rook
## Tips
* [rook.io](https://rook.io/) 
  * 存储管理框架
  * 以 CRD 的方式 文件、块、对象、NoSQL 存储服务
  * 支持管理服务
    * Ceph
      * 可以部署到磁盘
      * 可以部署到 Block PV
    * EdgeFS - 闭源 - 禁止商业使用
    * CockroachDB
    * Cassandra
    * NFS Server
      * 将 PVC 保留为 NFS 服务
    * Yugabyte DB
* 要求
  * k8s 1.11+
  * Ceph
    * 有原始块设备 - 没有分区没有格式化过的磁盘
    * 原始分区 - 没有文件系统
    * PV 能以 block 的模式工作
    * 安装 LVM
    * 使用 CSI 不要使用 FlexVolume
    * RBD `modprobe rbd`
    * CephFS 建议 Linux >= 4.17
  * NFS
    * 安装 nfs-utils
