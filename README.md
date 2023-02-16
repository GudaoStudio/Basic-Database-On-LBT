# Basic-Database-On-LBT

欢迎！

此仓库主要储存执行Ladybug、Honeybee-Energy、Honeybee-Radiance、Dragonfly时必不可少的可复用参数信息。  

它可以是Program Type、Loads、Schedule、Construction-Set、Construction、Modifie Set以及Modifie等复用率较高的内容。  也可以是明确了来源和具体使用范围的气象数据文件（.EPW File）及设计日文件（.DDY File）。

## 1  背景和基本规则

### 1.1  背景

在建筑节能设计中，如果根据不同地区的气候条件进行合理的节能设计，则可以有效地提高建筑能效，减少能源消耗，所以不同的地区会采用不同的节能措施，并且对于相关节能技术的主要技术指标，不同地区标准中的参考和限定数值也会有所不同。例如，寒冷地区的气温较低，采暖季较长，节能设计侧重点也是保温隔热、冬季供暖以及减少能源消耗，建筑需要采用高效保温材料、采暖设备的效率要求高等等，所以在相关地区的节能设计规范或标注中，建筑围护的传热系数规定通常会以一个较低的数值进行限制，以达到最低限度的建筑节能需求。

我国现行的国家及地方节能设计规范众多，根据《公共建筑节能设计标准》GB50189-2015的规定，建筑节能气候分区主要划分为严寒、寒冷、夏热冬冷、夏热冬暖以及温和地区5个区域。其中又因我国各省份幅员辽阔，同一地区的气候可能会出现些许差别，故又在5个节能气候分区的基础上又分为A、B、C区。不仅如此，对于不同的建筑，对节能设计的要求与侧重点也是不一样的。例如在节能设计中，通常将建筑的类型分为居住建筑、公共建筑和工业建筑三大类，每一种类型的建筑都又会有独立的要求。

由于这些因素，导致我国的节能设计规范、标准以及相关指导文件五花八门，能让人眼花缭乱，沉没在信息的海洋，也导致了行业模块化、数字化的标准化信息得不到有效的搜集，对于更能够利用新技术充当效率武器的绿色建筑与节能工程师来说，在工作的进程中如没有长时间的积累，重复的工作和枯燥的信息搜集工作会降低工程师的工作幸福感。

近年，正在开展行业规范的瘦身行动，例如在现行的《建筑节能与可再生能源利用通用规范》GB55015-2021中，统一规范了各建筑类型在不同建筑节能气候分区下的围护结构热工性能等信息，进一步集中并废止了此前了五花八门的部分标准规定。

可以通过行业变革的这个契机，通过Ladybug Tools这个模块化、参数化的工具来进行标准化的信息搜集，并通过开源的形式公布给所有行业的学生、教师、工程师等，促进行业的交流以及信息化的发展。

## 2  如何规范命名？

### 2.1  Program Type 的命名规则

Program Type 是用于记录空间的照明功率密度、设备功率密度、人员密度及散热量、新风量、房间夏季设定温度和冬季设定温度；照明开关时间、设备使用率、人员在室率、新风运行情况、供暖和空调系统运行时间、房间逐时温度；热水供应、燃气设备的供应、使用情况和外立面渗透等内扰因素的集合，是能耗模拟中的核心设置内容。

在Ladybug Tools中，Program Type 中包括了8种 Load 类型和与 Load 对应的 Schedule，是空间中涉及 Load 与 Schedule 的集合。

所以，为了使得 Load 和 Schedule 信息可追溯，所以在内容名称中，Program Type 的名称层级应要高于 Load 和 Schedule ，则可使用 HB ProgramType 组件进行设置，并将名称以如下结构表示：

` 标准号-标准年份::建筑类型::房间名称::其他内容 `

通过上述名称结构内容，以《民用建筑绿色性能计算标准》JGJ/T449-2018 附录C 建筑供暖和空调系统模拟计算运行参数 表C0.1-1中普通办公室的相关信息记录为如下形式：

` JGJ/T449-2018::办公建筑::普通办公室::外区 `

由于Ladybug Tools使用Python进行开发，需要考虑特殊符号、中文的兼容性问题，应在输入时对输入内容进行部分翻译，部分翻译后的形式如下所示：

` JGJ_T449-2018::Office Building::Ordinary Office::Perimeter `

#### 2.1.2  Load 的命名
Load（负荷）是指建筑系统所需的能量或功率，例如空调负荷、照明负荷等。Load对象用于描述建筑系统在不同时间段内的能量或功率需求，是进行能耗分析的重要组成部分之一。

在Ladybug Tools中，Load 用于设置空间的照明功率密度、设备功率密度、人员密度及散热量、新风量、房间夏季设定温度和冬季设定温度；照明开关时间、设备使用率、人员在室率、新风运行情况、供暖和空调系统运行时间、房间逐时温度；热水供应、燃气设备的供应、使用情况和外立面渗透等内扰因素。

它包括了8种 Load 类型，并与Schedule关联。为了使得与 Load 关联的 Schedule 的信息可追溯，所以在内容名称中，Load 的名称层级应要高于 Schedule ，则可通过如下名称结构表示：

例如将 Program Type 的案例进行延伸，需要设置照明功率密度和照明开关时间（或使用率）等信息，可使用 HB Lighting组件进行设置，并记录其名称为：

` JGJ_T449-2018::Office Building::Ordinary Office::Perimeter::Lighting `

拓展其案例，可按同一Program Type中涉及到不同 Load 的类型进行命名：

` JGJ_T449-2018::Office Building::Ordinary Office::Perimeter::People `  
` JGJ_T449-2018::Office Building::Ordinary Office::Perimeter::Equipment `  
` JGJ_T449-2018::Office Building::Ordinary Office::Perimeter::Ventilation `  
` JGJ_T449-2018::Office Building::Ordinary Office::Perimeter::Setpoint `  

#### 2.1.3  Schedule 的命名

Schedule用于设置各种不同类型的 Load ，描述模拟中不同参数随时间变化的规律性的对象，如室内温度、照明强度、空调运行状态等。通过定义Schedule对象，可以模拟建筑系统的运行，以及不同系统之间的相互作用。

将 Program Type 和 Load 的案例进行延伸，可使用 Honeybee 中提供的 Schedule 相关组件进行设置其计划并设置约束，记录其名称为：

`JGJ_T449-2018::Office Building::Ordinary Office::Perimeter::Lighting::Lighting Schedule`  
`JGJ_T449-2018::Office Building::Ordinary Office::Perimeter::People::Occupancy Schedule`  
` JGJ_T449-2018::Office Building::Ordinary Office::Perimeter::People::Activity Schedule `  
` JGJ_T449-2018::Office Building::Ordinary Office::Perimeter::Equipment::Equipment Schedule `  
` JGJ_T449-2018::Office Building::Ordinary Office::Perimeter::Ventilation::Ventilation Schedule `  
` JGJ_T449-2018::Office Building::Ordinary Office::Perimeter::Setpoint::Heating Schedule `  
` JGJ_T449-2018::Office Building::Ordinary Office::Perimeter::Setpoint::Cooling Schedule `  

### 2.2  Constitution Set 的命名规则

Construction Set是OpenStudio中的一个概念，类似于EnergyPlus中的Construction，但Set是一个更高层次的抽象，用于描述构造组件如何组合成建筑物。

构造集由多个构造组成，每个构造包含一个或多个材料。构造组件定义了建筑物的墙、屋顶、地板、窗户、门等元素的具体构造和材料热工性能，可以根据需要创建多个构造组件，并将它们组合成一个构造集。

通过使用Construction Set，可以快速创建建筑模型并进行建筑能耗模拟和分析。

` 标准号-标准年份::气候区::建筑类型::其他内容 `

#### 2.2.1  Construction 的命名

EnergyPlus中的Construction（构造）是指建筑物中各种建筑构件（例如墙、屋顶、地板、窗户、门等）的构造方式。每个构造对象由多个图层组成，每个图层由不同的材料（例如混凝土、玻璃、保温材料、石膏板等）组成。通过定义Construction，可以描述建筑物的墙、屋顶、地板、窗户、门等部分的具体构造，并将构造对象应用于建筑物的表面，通过计算建筑物的热传递和空气传递特性，从而进行建筑能耗模拟和分析。Construction通常需要与Construction Set或HB Obeject进行关联。

#### 2.2.2  Material 的命名

Material是用于定义建筑物内部或外部材料的对象，它包含了材料的物理和热学特性，包括密度、比热、热导率、吸收率、透射率等参数。通过定义Material，可以描述建筑物内部或外部的构造组成，如墙体、屋顶、地板、窗户、门等构造所使用的具体材料。Material对象通常需要Construction关联。

### 2.3  Modifier Set & Modifier 的命名规则

在Radiance中，Modifier是一种用于改变光照条件的对象，通常用于描述具有反射、折射、散射等特性的表面的光学特性。Modifier可以用于改变物件表面材质的反射率、透射率、粗糙度等属性，从而模拟不同光照条件下的表面反射、散射、透射现象。

## 3  如何提交？
