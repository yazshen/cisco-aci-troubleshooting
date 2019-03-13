## 避免使用VLAN Overlapping场景

### 1. 说明
在一个新的ACI项目中，通常我们会用传统网络的想法来规划和配置ACI上的EPG VLAN。但是，要避免一种情况：在一个EPG上重复定义相同的VLAN，这是VLAN Overlapping案例。

在思科官方文档已经明确，不建议客户使用这种案例，会导致BPDU异常，例如Block变成Forward，导致L2 Loop。

[思科官方文档](https://www.cisco.com/c/en/us/td/docs/switches/datacenter/aci/apic/sw/1-x/ACI_Best_Practices/b_ACI_Best_Practices/b_ACI_Best_Practices_chapter_010.html#id_39826)

VLAN pools containing overlapping encap block definitions should not be associated to the same AAEP (and subsequently the same leaf nodes). This can cause issues with BPDU forwarding through the fabric if the domains associated to an EPG have overlapping VLAN block definitions.

### 2. 配置案例

![VLAN-Overlapping](https://github.com/yazshen/cisco-aci-troubleshooting/blob/master/resource/VLAN-Overlapping-01.png)

### 3. 测试命令

![VLAN-Overlapping](https://github.com/yazshen/cisco-aci-troubleshooting/blob/master/resource/VLAN-Overlapping-02.png)

### 4. FD_VLAN
FD_VLAN
Flood domain VLAN. The FD-VLAN is the forwarding VLAN used to forward traffic on the Broadcom ASIC. The FD_VLAN is directly linked to the ACCESS_ENC and is also referred to as the internal VLAN. The FD_VLAN is used to represent the ACCESS_ENC instead of linking it directly to the BD_VLAN. The FD_VLAN allows the BD_VLAN to link to different ACCESS_ENCs and treat all of them as if they were all in the same 802.1Q VLAN on a NX-OS switch. When a broadcast packet comes into the leaf switch from the ACI fabric, the BD_VLAN can map to several FD_VLANs to allow the packet to be forwarded out different ports using different ACCESS_ENCs. The FD_VLAN is used to learn Layer 2 MAC addresses.

在测试命令里面，我们可以看到2台Leaf交换机上，VLAN 170的FD_ENCAP数值不一致，这样就会导致BPDU异常，Block变成Forward，引起L2 Loop。
