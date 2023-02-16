# Basic-Database-On-LBT

此仓库主要储存执行Ladybug、Honeybee-Energy、Honeybee-Radiance、Dragonfly时必不可少的可复用参数信息。  

可以是Program Type、Loads、Schedule、Construction-Set、Construction、Modifie Set以及Modifie等复用率较高的内容。  
也可以是明确了来源和具体使用范围的气象数据文件（.EPW File）及设计日文件（.DDY File）。 

## 1  如何规范命名？

### 1.1  Program Type

Program Type 通常用于记录某个空间的照明功率密度、设备功率密度、人员密度及散热量、新风量、房间夏季设定温度和冬季设定温度；照明开关时间、设备使用率、人员在室率、新风运行情况、供暖和空调系统运行时间、房间逐时温度；热水供应、燃气设备的供应、使用情况和外立面渗透等内扰因素，是能耗模拟中的核心设置内容。

在Ladybug Tools中，Program Type 中包括了8种 Load 类型和与 Load 对应的 Schedule，是空间中涉及 Load 与 Schedule 的集合。

所以，为了使得 Load 和 Schedule 信息可追溯，所以在内容名称中，Program Type 的名称层级应要高于 Load 和 Schedule ，则可通过如下名称结构表示：

` 标准号-标准年份::建筑类型::房间名称::其他内容 `

通过上述名称结构内容，以《民用建筑绿色性能计算标准》JGJ/T449-2018 附录C 建筑供暖和空调系统模拟计算运行参数 表C0.1-1中普通办公室的相关信息记录为如下形式：

` JGJ/T449-2018::办公建筑::普通办公室::外区 `

由于Ladybug Tools使用Python进行开发，需要考虑特殊符号、中文的兼容性问题，应在输入时对输入内容进行部分翻译，部分翻译后的形式如下所示：

` JGJ_T449-2018::Office Building::Ordinary Office::Perimeter `

### 1.2  Schedule

# 2  如何提交？
