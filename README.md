# Basic-Database-On-LBT
欢迎！此仓库主要储存执行Ladybug、Honeybee-Energy、Honeybee-Radiance、Dragonfly时必不可少的可复用参数信息。  

它可以是 Program Type、Loads、Schedule、Construction-Set、Construction、Modifie Set 以及 Modifie 等复用率较高的内容。也可以是明确了来源和具体使用范围的气象数据文件（.EPW File）及设计日文件（.DDY File）。

目前，更新主要以Program Type为主，Construction-Set、Construction会随机更新。

# 1  预计更新计划

由于我个人经历和能力有限，所以目前仅承诺在空闲时间中更新如下内容，如更新完毕会用删除线标明：

- [x] ~~符合《建筑节能与可再生能源利用通用规范》GB55015-2021 附录 C 的 Program Type~~
- [x] ~~符合《民用建筑绿色性能计算标准》JGJ/T 449-2018 附录 C 的 Program Type（除居住建筑）~~。
- [x] ~~符合《建筑围护结构节能工程做法及数据》09J908-3 的标准做法的 Construction.
- [x] ~~建筑门窗节能性能标识网中标识产品目录中的提供节能门窗参数，按U值、SHGC值以及标签序号排列（详尽名称无法填写，允许字符有限）~~
- [ ] 符合《近零能耗建筑技术标准》GB/T 51350-2019 附录 A 的 Program Type

- [ ] 符合《建筑节能与可再生能源利用通用规范》GB55015-2021 3.1 建筑和围护结构规定的 Construction Set

# 2  编码对照

###  2.1  编码规则

1. **一级编码**：建筑大类使用英文全称.

2. **二级编码**：

   ```
   A  - 严寒、寒冷地区  
   B  - 夏热冬冷、夏热冬暖、温和地区  
   OP - 门诊楼（Outpatient）  
   IP - 住院部（Inpatient）  
   TC - 教学楼（Teaching Classroom）
   ```

   

3. **三级编码**：

   ```
   BR - 卧室（Bedroom）  
   LR - 起居室（Living Room）  
   KT - 厨房（Kitchen）  
   BT - 卫生间（Bathroom）  
   SR - 辅助房间（Service Room）  
   a  - <500m²  
   b  - 501~1000m²  
   c  - 1001~1500m²  
   d  - 1501~2000m²  
   e  - 2001~2500m²  
   f  - 2501~3000m²  
   g  - >3000m²
   ```

   

### 2.2  GB55015 - 2021 完整编码对照表

| 原始中文名称                                     | 英文全称+编码      |
| :----------------------------------------------- | :----------------- |
| 办公建筑                                         | `Office`           |
| 旅馆建筑                                         | `Hotel`            |
| 商业建筑                                         | `Commercial`       |
| 医院建筑-门诊楼                                  | `Hospital-OP`      |
| 医院建筑-住院部                                  | `Hospital-IP`      |
| 学校建筑-教学楼                                  | `School-TC`        |
| 居住建筑 - 严寒、寒冷地区 - 卧室                 | `Residential-A-BR` |
| 居住建筑 - 严寒、寒冷地区 - 起居室               | `Residential-A-LR` |
| 居住建筑 - 严寒、寒冷地区 - 厨房                 | `Residential-A-KT` |
| 居住建筑 - 严寒、寒冷地区 - 卫生间               | `Residential-A-BT` |
| 居住建筑 - 严寒、寒冷地区 - 辅助房间             | `Residential-A-SR` |
| 居住建筑 - 夏热冬冷、夏热冬暖、温和地区 - 卧室   | `Residential-B-BR` |
| 居住建筑 - 夏热冬冷、夏热冬暖、温和地区 - 起居室 | `Residential-B-LR` |
| 居住建筑 - 夏热冬冷、夏热冬暖、温和地区 - 厨房   | `Residential-B-KT` |
| 工业建筑（＜500m²）                              | `Industrial-a`     |
| 工业建筑（501~1000m²）                           | `Industrial-b`     |
| 工业建筑（1001~1500m²）                          | `Industrial-c`     |
| 工业建筑（1501~2000m²）                          | `Industrial-d`     |
| 工业建筑（2001~2500m²）                          | `Industrial-e`     |
| 工业建筑（2501~3000m²）                          | `Industrial-f`     |
| 工业建筑（＞3000m²）                             | `Industrial-g`     |



# 3  如何使用这个库中分享的文件？

目前，本仓库的所有资源会随着 Polliantion 一键安装包一同安装到用户的设备当中，用户仅需通过文本输入（需要名称完备）或通过 HB Search 相关组件输入关键词搜索调用。

- GB55015-2021
- JGJ/T 449-2018

![image](https://github.com/GudaoStudio/Basic-Database-On-LBT/assets/51848364/7078bd8e-d510-4358-a0a8-750e723ed97a)

# 4 已知但无法解决的问题

## 4.1  游泳馆冬季设定温度大于夏季设定温度
《民用建筑绿色性能计算标准》JGJ/T 449-2018 附录 C 第60页出现了冬季设定温度大于夏季设定温度的情况，该情况会造成Energyplus计算失败，且不能通过标准化的 Program Type 进行修正。
![image](https://github.com/GudaoStudio/Basic-Database-On-LBT/assets/51848364/41f6cb7f-9158-4edf-a9a1-337728e95182)
