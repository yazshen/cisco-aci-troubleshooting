## 无法通过OOB用SSH访问Spine和Leaf

通常在ACI的新项目中，经常会碰到这样的情况：正确配置了Spine和Leaf上的OOB地址，但是为什么无法用SSH登录: ssh admin@<spine or leaf OOB address>

### 1. 检查SSH服务是否正常
+ SSH登录到APIC服务器
+ 直接使用ssh命令测试是否可以通过NodeName登录到Spine和Leaf交换机
![Mgmt-OOBSubnet](https://github.com/yazshen/cisco-aci-troubleshooting/blob/master/resource/Mgmt-OOBSubnet-01.png)

+ ssh命令测试使用OOB登录到Spine和Leaf交换机，失败，无法登录
![Mgmt-OOBSubnet](https://github.com/yazshen/cisco-aci-troubleshooting/blob/master/resource/Mgmt-OOBSubnet-02.png)

### 2. 检查APIC上mgmt租户配置
+ 通过APIC管理页面，访问：Tenant -> mgmt -> External Management Network Instance Profiles，进入Profile
![Mgmt-OOBSubnet](https://github.com/yazshen/cisco-aci-troubleshooting/blob/master/resource/Mgmt-OOBSubnet-03.png)

+ 我们发现Subnet配置为空，Subnet定义了访问控制，哪些外部地址可以通过OOB访问ACI Fabric

### 3. 测试SSH通过OOB访问
+ 没有特殊的安全策略要求，我们配置0.0.0.0/0，测试SSH到OOB地址，访问正常
![Mgmt-OOBSubnet](https://github.com/yazshen/cisco-aci-troubleshooting/blob/master/resource/Mgmt-OOBSubnet-04.png)
