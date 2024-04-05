#Crazyflie 2.1 kit user manual

#安全与常规信息
Crazyflie 2.1是Bitcraze AB设计，中国组装。

#声明


本文档中的信息如有更改，恕不另行通知。Bitcraze AB 假设对任何遗漏或不准确概不负责，并明确表示
不承担任何责任，因以下原因直接或间接造成的损失或风险，无论是个人的还是其他的使用本文档的任何
内容。请联系 Bitcraze AB 获取最新信息本文档的版本。
FCC声明

出于监管识别目的，Crazyflie 2.1 的型号为 CF21KIT。Crazyflie 2.1 FCC ID 为 2AUV3CF21KIT。此
FCC ID 只能印在产品包装盒上。

This device complies with Part 15 of the FCC Rules. Operation is subject to the following
two conditions: (1) this device may not cause harmful interference, and (2) this device must
accept any interference received, including interference that may cause undesired operation.
Changes or modifications not expressly approved by the party responsible for compliance
could void the user's authority to operate the equipment.
本设备符合 FCC 规则的第 15 部分。操作须遵守以下规定两个条件：
（1） 本设备不会造成有害干扰，以及 
（2） 本设备必须接受接收到的任何干扰，包括可能导致意外操作的干扰。未经合规责任方明确批准的更改或修改
可能会使用户操作设备的权限失效。

根据美国联邦通信委员会规则第15部分的规定，该设备经过测试，符合B类数字设备的限制。这些限制旨在提供合理的保
护，防止住宅安装中的有害干扰。该设备产生、使用并可辐射射频能量，如果不按照说明安装和使用，可能会对无线电
通信造成有害干扰。但是，不能保证在特定的安装中不会发生干扰。如果该设备确实对无线电或电视接收造成有害干扰，
可以通过关闭和打开设备来确定，则鼓励用户尝试通过以下一种或多种措施来纠正干扰：
● 重新定向或重新定位接收天线。
● 增加设备和接收器之间的间距。
● 请咨询经销商或有经验的收音机/电视技术人员以获得帮助

安全预防措施
在使用Crazyflie之前，请阅读并遵循本手册。如果Crazyflie已经损坏，请不要使用。
小心处理电池组。该产品包含锂离子聚合物电池。
如果蓄电池处理不当，则有发生火灾和烧伤的风险。

警告
为避免损坏产品或电池，本产品只能与兼容电池一起使用。
警告：为了降低火灾或烧伤的风险，请勿拆卸、挤压、刺穿、短路外部触点或电路、暴露在60°C（140°F）以上的温度下，
或在火或水中处理。不要将蓄电池暴露在极低的空气压力下，因为这可能导致爆炸或易燃液体或气体泄漏。

根据当地法规或随产品提供的参考指南回收或处理用过的电池。
如果用不正确的型号更换电池，则有爆炸的风险。处置
根据说明使用过的电池

警告：请勿在以下“规格”部分指定的温度范围之外操作Crazyflie。
警告：请勿在无人看管的情况下对Crazyflie充电。