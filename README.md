# cisco-aci-troubleshooting
Cisco ACI 经验分享

作者：Robbie Shen (yazshen@cisco.com)

## 正文
### 1. ACI运维三要素
+ 使用GUI配置ACI   
+ 检查Fault、对象健康值
+ 使用CLI校验功能

Cisco ACI作为一个SDN产品，支持使用GUI, CLI, RESTFUL API来配置相关功能，但是推荐使用GUI方式配置。RESTFUL API偏向北向集成，常用于batch configuration。

配置完成后，首先需要检查是否有Fault信息产生、相关对象健康值是否有变化。

最后，我们到APIC或N9K的CLI界面，相关功能校验和确认配置是否生效。

### 2. 经验分享
[Cisco ACI安装配置Guide](https://github.com/syz2000/cisco-aci-troubleshooting/blob/master/new-installation.md)

[L3out Transit Route](https://github.com/syz2000/cisco-aci-troubleshooting/blob/master/L3out-TransitRoute.md)

[无法通过OOB用SSH访问Spine和Leaf](https://github.com/syz2000/cisco-aci-troubleshooting/blob/master/Mgmt-OOBSubnet.md)

[EPG中组播配置：PIM ASM和SSM](https://github.com/syz2000/cisco-aci-troubleshooting/blob/master/Feature-PIM.md)

[Bridge Domain的Static Route功能介绍](https://github.com/syz2000/cisco-aci-troubleshooting/blob/master/L3out-StaticRouteBD.md)

[避免使用VLAN Overlapping场景](https://github.com/syz2000/cisco-aci-troubleshooting/blob/master/VLAN-Overlapping.md)

[L3out如何修改OSPF Type](https://github.com/syz2000/cisco-aci-troubleshooting/blob/master/L3out-OSPF-Type2.md)



## License
GNU General Public License v3.0
(https://github.com/syz2000/cisco-aci-troubleshooting/blob/master/LICENSE)
