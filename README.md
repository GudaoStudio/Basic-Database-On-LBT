# Basic-Database-On-LBT

此仓库主要储存执行Ladybug、Honeybee-Energy、Honeybee-Radiance、Dragonfly时必不可少的可复用参数信息。  

可以是Program Type、Loads、Schedule、Construction-Set、Construction、Modifie Set以及Modifie等复用率较高的内容。  
也可以是明确了来源和具体使用范围的气象数据文件（.EPW File）及设计日文件（.DDY File）。 

## 1  如何规范命名？

### 1.1  Program Type

Program Type 通常用于记录某个空间的照明功率密度、设备功率密度、人员密度及散热量、新风量、房间夏季设定温度和冬季设定温度；照明开关时间、设备使用率、人员在室率、新风运行情况、供暖和空调系统运行时间、房间逐时温度；热水供应、燃气设备的供应、使用情况和外立面渗透等内扰因素。
<center> 标准号-标准年份::建筑类型::房间名称::其他备注 </center>

例如，以《民用建筑绿色性能计算标准》JGJ/T449-2018 附录C 建筑供暖和空调系统模拟计算运行参数中的表C0.1-1的相关内容为例：
可将表C0.1-1记录为如下形式：

<center> JGJ/T449-2018::办公建筑::普通办公室::外区 </center>

由于Ladybug Tools使用Python进行开发，需要考虑特殊符号、中文的兼容性问题，应在输入时对输入内容进行部分翻译，部分翻译后的形式如下所示：

<center> JGJ_T449-2018::Office Building::Ordinary Office::Perimeter </center>

### 1.2  Schedule

# 2  如何提交？