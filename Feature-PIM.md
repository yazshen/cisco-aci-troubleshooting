## EPG中组播配置：PIM ASM和SSM
系统配置
+ ACI版本：3.2(2o)
+ 硬件型号：93180YC-EX
+ VRF-PIM: BD-PIM01, BD-PIM02
+ BD-PIM01: EPG 192.168.101.x, subnet 192.168.101.254/24
+ BD-PIM02: EPG 192.168.102.x, subnet 192.168.102.254/24
+ EPG 192.168.101.x: EP 192.168.101.1 from Leaf13 Eth 1/42
+ EPG 192.168.102.x: EP 192.168.102.1 from Leaf13 Eth 1/41, EP 192.168.102.2 from Leaf14 Eth 1/41

拓扑图
![PIM ASM 场景一](https://github.com/syz2000/cisco-aci-troubleshooting/blob/master/resource/Feature-PIM-01.png)

### 1. PIM ASM 场景一
在EPG内，EP 192.168.102.1作为Sender，EP 192.168.102.1和192.168.102作为Receiver

Sender在交换机A，Receiver在交换机A和B

测试软件：iperf version 2.0.5 (08 Jul 2010) pthreads on CentOS 7

配置：
+ 在Bridge Domain下面启用PIM
![PIM ASM 场景一](https://github.com/syz2000/cisco-aci-troubleshooting/blob/master/resource/Feature-PIM-02.png)

测试：
+ 192.168.102.2加入组播地址224.0.101.1
![PIM ASM 场景一](https://github.com/syz2000/cisco-aci-troubleshooting/blob/master/resource/Feature-PIM-03.png)

+ 192.168.102.1发送数据到组播地址224.0.101.1
![PIM ASM 场景一](https://github.com/syz2000/cisco-aci-troubleshooting/blob/master/resource/Feature-PIM-04.png)

  ![PIM ASM 场景一](https://github.com/syz2000/cisco-aci-troubleshooting/blob/master/resource/Feature-PIM-05.png)

### 2. PIM ASM 场景二
在EPG之间，EP 192.168.101.1作为Sender，EP 192.168.102.2作为Receiver

Sender在交换机A，Receiver在交换机B

测试软件：iperf version 2.0.5 (08 Jul 2010) pthreads on CentOS 7

配置：
+ 在两个Bridge Domain下面都启用PIM
+ 在VRF下面启用Multicast
![PIM ASM 场景二](https://github.com/syz2000/cisco-aci-troubleshooting/blob/master/resource/Feature-PIM-06.png)

+ 配置Static RP为192.168.101.1
![PIM ASM 场景二](https://github.com/syz2000/cisco-aci-troubleshooting/blob/master/resource/Feature-PIM-07.png)

测试：
+192.168.102.1和192.168.102.2加入组播地址224.0.101.1
![PIM ASM 场景二](https://github.com/syz2000/cisco-aci-troubleshooting/blob/master/resource/Feature-PIM-08.png)

+192.168.101.1发送数据到组播地址224.0.101.1
![PIM ASM 场景二](https://github.com/syz2000/cisco-aci-troubleshooting/blob/master/resource/Feature-PIM-09.png)


### 3. PIM SSM 场景一
在EPG内，EP 192.168.102.1作为Sender，EP 192.168.102.1和192.168.102作为Receiver

Sender在交换机A，Receiver在交换机A和B

测试软件：iperf version 2.0.5 (08 Jul 2010) pthreads on CentOS 7

配置：
+ 在Bridge Domain下面启用PIM
![PIM SSM 场景一](https://github.com/syz2000/cisco-aci-troubleshooting/blob/master/resource/Feature-PIM-02.png)

+ 在Policies -> Protocol -> IGMP Interface下创建新的策略
![PIM SSM 场景一](https://github.com/syz2000/cisco-aci-troubleshooting/blob/master/resource/Feature-PIM-10.png)

+ 在Bridge Domain下关联新创建的IGMP策略
![PIM SSM 场景一](https://github.com/syz2000/cisco-aci-troubleshooting/blob/master/resource/Feature-PIM-11.png)
