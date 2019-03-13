## L3out如何修改OSPF Type

### 1. 在ACI L3out中默认OSPF宣告路由为Type-2
![L3out-OSPF-Type2](https://github.com/yazshen/cisco-aci-troubleshooting/blob/master/resource/L3out-OSPF-Type2-01.png)

### 2. 修改OSPF宣告路由为Type-1
官方文档只有在Transit Route提到了如何配置Type-1, Type2
[L3out-OSPF-Type2](https://www.cisco.com/c/en/us/td/docs/switches/datacenter/aci/apic/sw/2-x/L3_config/b_Cisco_APIC_Layer_3_Configuration_Guide/b_Cisco_APIC_Layer_3_Configuration_Guide_chapter_010100.html#concept_A3BD730B9A9F4A53A9D3B5553F6AC61D)

如果我们没有Transit Route，是否就不行了呢？答案是：也可以做。

我们需要把EPG网络按照Transit Route配置定义并配置Route Control Profile
![L3out-OSPF-Type2](https://github.com/yazshen/cisco-aci-troubleshooting/blob/master/resource/L3out-OSPF-Type2-02.png)

检查远端路由表，确定收到了Type-1的路由信息
![L3out-OSPF-Type2](https://github.com/yazshen/cisco-aci-troubleshooting/blob/master/resource/L3out-OSPF-Type2-03.png)

