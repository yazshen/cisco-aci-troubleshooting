## Bridge Domain的Static Route功能
### 官方文档
https://www.cisco.com/c/en/us/td/docs/switches/datacenter/aci/apic/sw/2-x/L3_config/b_Cisco_APIC_Layer_3_Configuration_Guide/b_Cisco_APIC_Layer_3_Configuration_Guide_chapter_01000.html

###功能介绍
从ACI 3.0开始，我们可以不需要配置L3out，直接在BD/EPG下面配置一个静态路由（仅限/32）。一般来说，用于防火墙后面的虚拟服务。

### 功能配置
配置
+ 在EPG的Subnet下面，添加192.168.99.101/32路由，下一跳地址为192.168.101.1
![Static Route on BD](https://github.com/yazshen/cisco-aci-troubleshooting/blob/master/resource/L3out-StaticRouteBD-01.png)

+ iping测试
![Static Route on BD](https://github.com/yazshen/cisco-aci-troubleshooting/blob/master/resource/L3out-StaticRouteBD-02.png)

+ show ip route命令是看不到192.168.101/32路由
![Static Route on BD](https://github.com/yazshen/cisco-aci-troubleshooting/blob/master/resource/L3out-StaticRouteBD-03.png)

+ 通过show ip static-route命令来检查路由表
![Static Route on BD](https://github.com/yazshen/cisco-aci-troubleshooting/blob/master/resource/L3out-StaticRouteBD-04.png)

+ 通过show endpoint ip 192.168.99.101命令来检查EP表
![Static Route on BD](https://github.com/yazshen/cisco-aci-troubleshooting/blob/master/resource/L3out-StaticRouteBD-05.png)
