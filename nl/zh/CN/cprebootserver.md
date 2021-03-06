---

copyright:

  years: 1994, 2019

lastupdated: "2018-02-25"

keywords: rescue kernel, command line, restart command

subcollection: customer-portal 

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:tip: .tip}
{:screen: .screen}
{:new_window: target="_blank"}

# 重新引导服务器
{: #customerportal_rebootserver}

有时，{{site.data.keyword.BluSoftlayer_notm}} 基础架构中发生的事件需要重新启动服务器。
{:shortdesc}

使用以下步骤重新启动服务器：
1. 在客户门户网站中，单击**支持**选项卡。
2. 单击**重新引导**。
3. 选择要重新启动的服务器，然后单击**重新引导**。
4. 选择下列某种方法来重新启动服务器：

  * 缺省（先尝试使用 IPMI 重新启动，然后尝试使用电源板进行重新启动）
  * IPMI
  * 电源板
5. 单击**重新引导**。

此页面还提供了引导至急救内核的功能，如果您遇到因配置问题而导致服务器无法引导至操作系统的问题，此功能会非常有用。引导至急救内核后，可以装载服务器的一个或多个驱动器，然后修复配置问题。问题修复后，可以通过命令行重新启动服务器，服务器将重新启动至服务器的缺省内核。发出重新启动命令后，您将看到预计完成时间。
