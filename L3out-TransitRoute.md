## L3out Transit Route 配置

### 1. 官方文档链接
[https://www.cisco.com/c/en/us/td/docs/switches/datacenter/aci/apic/sw/2-x/L3_config/b_Cisco_APIC_Layer_3_Configuration_Guide/b_Cisco_APIC_Layer_3_Configuration_Guide_chapter_010100.html](https://www.cisco.com/c/en/us/td/docs/switches/datacenter/aci/apic/sw/2-x/L3_config/b_Cisco_APIC_Layer_3_Configuration_Guide/b_Cisco_APIC_Layer_3_Configuration_Guide_chapter_010100.html "Cisco Official Guide")

### 2. 拓扑图
![L3out-TransitRoute](https://github.com/syz2000/cisco-aci-troubleshooting/blob/master/resource/L3out-TransitRoute.png)

### 3. 配置
Transit Route类似传统网络里面的路由重分发，通过ACI Fabric，不同的L3out网络可以互相访问


例如，OSPF网络192.168.1.1/32访问静态路由网络（一般为互联网区域）上8.8.8.8/32


进入L3out-OSPF配置下的External EPG，然后把8.8.8.8/32加入subnet
+ 勾选：Export Route Control Subnet
+ 取消：External Subnets for the External EPG（因为我们配置的8.8.8.8/32并不是External EPG所属的路由)
![L3out-TransitRoute](https://github.com/syz2000/cisco-aci-troubleshooting/blob/master/resource/L3out-01.png)


登录到OSPF路由器，检查路由表
![L3out-TransitRoute](https://github.com/syz2000/cisco-aci-troubleshooting/blob/master/resource/L3out-02.png)


使用Ping测试
![L3out-TransitRoute](https://github.com/syz2000/cisco-aci-troubleshooting/blob/master/resource/L3out-03.png)
