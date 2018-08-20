# cisco-aci-troubleshooting
Cisco ACI 经验分享 (Robbie Shen)

## 正文
### 1. ACI运维三要素
+ 使用GUI配置ACI   
+ 检查Fault、对象健康值
+ 使用CLI校验功能

Cisco ACI作为一个SDN产品，支持使用GUI, CLI, RESTFUL API来配置相关功能，但是推荐使用GUI方式配置。RESTFUL API偏向北向集成，常用于batch configuration。

配置完成后，首先需要检查是否有Fault信息产生、相关对象健康值是否有变化。

最后，我们到APIC或N9K的CLI界面，相关功能校验和确认配置是否生效。

### 2. 经验分享
[L3out Transit Route](https://github.com/syz2000/cisco-aci-troubleshooting/blob/master/L3out-TransitRoute.md)


