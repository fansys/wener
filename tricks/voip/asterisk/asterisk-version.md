---
id: version
title: Asterisk 版本
---

# Asterisk Version

## Tips
* [Versions](https://wiki.asterisk.org/wiki/display/AST/Asterisk+Versions)
* [CHANGES](https://github.com/asterisk/asterisk/blob/master/CHANGES)
* [edge/main/x86_64/asterisk](https://pkgs.alpinelinux.org/package/edge/main/x86_64/asterisk)
  * edge 版
* JIRA [Change Log](https://issues.asterisk.org/jira/browse/ASTERISK/?selectedTab=com.atlassian.jira.jira-projects-plugin:changelog-panel)
* [res_pjsip: Enable DNS support.](https://reviewboard.asterisk.org/r/3343/diff/)

## 17

### 新增
* ARI 支持应用事件过滤
* AttendedTransfer
* BlindTransfer
* ConfBridge
  * remb_behavior 选项新增 average_all, highest_all, lowest_all
    * bridge 级别而不是每个来源级别控制
* Dial
  * RINGTIME 和 RINGTIME_MS 变量 - 秒和毫秒 - 创建通话通道和收到第一个 RINGING 信号的间隔
  * PROGRESSTIME 和 PROGRESSTIME_MS - 同上 - 处理 PROGRESS 信号 - 最低值应该为 PDD (Post Dial Delay)
  * DIALEDTIME_MS 和 ANSWEREDTIME_MS - DIALEDTIME 和 ANSWEREDTIME 的毫秒版本
* RTP/ICE
  * 可以使用 ice_host_candidate 本地地址
* DUNDi
  * 支持 IPv4/IPv6 双绑定
* 新增 res_mwi_devstate 模块
  * 订阅语音信箱状态事件
* [Prometheus](https://wiki.asterisk.org/wiki/display/AST/Asterisk+17+Configuration_res_prometheus) exporter

## 16 / LTS / 2018-10-09 - 2022-10-09
* LTS 版本
* PG 12 https://github.com/asterisk/asterisk/commit/52ade18420b346449dff40d6bdb071444cf29e2d

### 新增
* WebRTC
  * 提示视频质量
  * 支持 REMB
    * 聚合预估每个客户端的可用带宽反馈给发送方 - 发送方可以此来调整包大小
  * 支持 NACK
    * 允许客户端请求重新发送来实现更好的乱序包处理
* PJSIP
  * 性能提升 - 允许更多的 AOR 且不影响启动时间
* ConfBridge
  * 文本消息会被中继转发 - 如果开启了 enable_events 还会发送 JSON 事件
* app_originate 支持 `a` 参数, 异步拨号, 不等待响应
* app_macro 模块废弃, 使用 app_stack (Gosub)
* res_config_sqlite 模块废弃, 使用 res_config_sqlite3
* res_monitor 模块废弃, 使用 app_mixmonitor
* cdr_syslog 模块废弃, 并且默认不会构建
* app_fax 模块废弃, 使用 res_fax

* 16.7
* 16.6.2

### 15
* 默认使用 bundled pjproject
* 支持 RTCP Multiplexing 和 BUNDLE
  * [Multiplexing RTP Data and Control Packets on a Single Port](https://tools.ietf.org/html/rfc5761)
  * [Negotiating Media Multiplexing Using the SDP](https://datatracker.ietf.org/doc/draft-ietf-mmusic-sdp-bundle-negotiation/)
* Unified Plan
  * [A Unified Plan for Using SDP with Large Numbers of Media Flows draft-roach-mmusic-unified-plan-00](https://tools.ietf.org/html/draft-roach-mmusic-unified-plan-00)
  * multiple media streams per connection
* [asterisk/cyber_mega_phone_2k](https://github.com/asterisk/cyber_mega_phone_2k)
  * testing of Asterisk's (15+) multistream capabilities

### 14
* 14.6.2 - 2017-09-19
* 14.6.1 - 2017-08-31
  * [5902](https://gerrit.asterisk.org/#/c/5902/) res_pjsip: `dtmf_mode` 添加 `auto_info`
      * 默认的 `auto` 会将 dtmf 模式回退到 inband, 该模式是回退为 `INFO`
  * [ASTERISK-27152] - Sending a "tel" uri in a From or To header in an unauthenticated message causes asterisk to crash
* 14.6.0
  * [ASTERISK-22432] - Async AGI crashes Asterisk when issuing "set variable" command without args
  * [ASTERISK-26978] - rtp: Crash in ast_rtp_codecs_payload_code()
  * [ASTERISK-27016] - Crash occurs when a channel in a 'mixing,dtmf_events' bridge is muted multiple times.
  * [ASTERISK-27026] - res_ari: Crash when no ari.conf configuration file exists
  * [ASTERISK-27050] - Crash on Transcoded Audio in PERIODIC_HOOK Function
  * [ASTERISK-27108] - Crash using 'data get' CLI command
  * [ASTERISK-25370] - res_corosync segfaults at startup with corosync version > 2.x
  * [ASTERISK-27046] - res_pjsip_transport_websocket: segfault in get_write_timeout
  * [ASTERISK-27057] - Seg Fault in ast_sorcery_object_get_id at sorcery.c
* 14.5.0
  * [ASTERISK-21855] - Asterisk crashes when XMPP message is sent (JabberSend) and no internet connection is available
  * [ASTERISK-26692] - res_rtp_asterisk: Crash in dtls_srtp_handle_timeout at res_rtp_asterisk (using chan_sip)
  * [ASTERISK-26835] - res_rtp_asterisk: Crash when freeing RTCP address string
  * [ASTERISK-26853] - res_rtp_asterisk: Crash in pjnath when receiving packet
  * [ASTERISK-26926] - func_speex: Crash caused by frame with no datalen
  * [ASTERISK-26927] - pjproject_bundled: Crash on pj_ssl_get_info() while ioqueue_on_read_complete().
  * [ASTERISK-26953] - Asterisk crash if hep.conf have some missing parameters
  * [ASTERISK-26983] - Crash in Manager Reload when TLS Config Changes
  * [ASTERISK-25506] - [patch]CONFBRIDGE failure after an app_confbrige.so module reload results in segfault or error/warning messages.
  * [ASTERISK-26606] - tcptls: Incorrect OpenSSL function call leads to misleading error report

## 13
* REST
* WebSocket
* Stasis
