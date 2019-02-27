## Cisco ACI安装和配置
### 1. 安装前准备工作
#### 1.1 ACI软件版本
ACI软件官方下载链接：[ACI Software Download](https://software.cisco.com/download/home/285968390/type)

+ 软件文件说明

APIC Image for 3.2(4e) Release (aci-apic-dk9.3.2.4e.iso): 版本号为3.2(4e)，用于安装和升级APIC服务器

Cisco Nexus 9000 Series ACI Mode Switch Software Release 13.2(4e) (aci-n9000-dk9.13.2.4e.bin): 版本号为13.2(4e)，用于安装和升级Cisco Nexus 9K交换机

+ 软件版本说明

Cisco官方要求：整个ACI Fabric里面只能运行一个软件版本，也就是说APIC和N9K交换机上版本必须一致

N9K交换机版本号会在ACI版本号前面多一个"1"，例如：13.2(4e)等于ACI 3.2(4e)

#### 1.2 APIC CIMC版本
APIC服务器是Cisco UCS C-Series产品定制，CIMC是UCS服务器上的带外管理系统。

Cisco官方针对每一个ACI软件版本都会有一个推荐CIMC版本，建议用户使用推荐版本。我们可以在Release Notes文档里面找到相关版本信息，例如: [3.2(4e)](https://www.cisco.com/c/en/us/td/docs/switches/datacenter/aci/apic/sw/3-x/release_notes/Cisco-APIC-Release-Notes-324.html)

```

This release supports the following firmware:

—      3.0(4d) CIMC HUU ISO (recommended)

—      For UCS C220/C240 M4: 3.0(3f) CIMC HUU ISO

—      For UCS C220/C240 M3: 3.0(3e) CIMC HUU ISO

—      2.0(13i) CIMC HUU ISO

—      2.0(9c) CIMC HUU ISO

—      2.0(3i) CIMC HUU ISO

```

#### 1.3 推荐版本

从刚才的官方链接我们可以看的，目前ACI有1.x, 2.x, 3.x, 4.x这4个大版本，每个大版本下面都有不少MR版本。那么到底如何选择呢？

+ 1.x 已经EOS，不需要再考虑了

[ACI 1.x EOS](https://www.cisco.com/c/en/us/products/collateral/cloud-systems-management/application-policy-infrastructure-controller-apic/eos-eol-notice-c51-740340.html)

+ 官方推荐2.x, 3.x

[Recommended ACI Software Release](https://www.cisco.com/c/en/us/td/docs/switches/datacenter/aci/apic/sw/recommended-release/b_Recommended_Cisco_ACI_Releases.html)

选择好大版本之后，再选择最新的MR版本

+ 不要选择已经标注为Deferred Release的版本


### 2. 升级CIMC
#### 2.1 查看UCS服务器型号和规格

首选，登录CIMC管理界面，找到Server Summary -> Server Properties
![UCS Type Model](https://github.com/syz2000/cisco-aci-troubleshooting/blob/master/resource/new-installation-01.png)

从BIOS Version中我们可以知道这台APIC-SERVER-M1的型号为Cisco UCS C220M3

从UCS产品页面下载CIMC安装介质：[UCS CIMC Download](https://software.cisco.com/download/home/283612685)

选择"Unified Computing System (UCS) Server Firmware":
![CIMC Firmware](https://github.com/syz2000/cisco-aci-troubleshooting/blob/master/resource/new-installation-02.png)

#### 2.2 使用Virtual KVM更新CIMC
我们可以使用Local KVM with DVD，Virtual KVM方式来重启服务器并用CIMC介质启动，升级CIMC相关固件时候，建议Update ALL

输入默认密码：password

![CIMC Firmware](https://github.com/syz2000/cisco-aci-troubleshooting/blob/master/resource/new-installation-03.png)

选择Cisco vKVM-Mapped vDVD

![CIMC Firmware](https://github.com/syz2000/cisco-aci-troubleshooting/blob/master/resource/new-installation-04.png)

CIMC引导中

![CIMC Firmware](https://github.com/syz2000/cisco-aci-troubleshooting/blob/master/resource/new-installation-05.png)

选择Update All

![CIMC Firmware](https://github.com/syz2000/cisco-aci-troubleshooting/blob/master/resource/new-installation-06.png)



