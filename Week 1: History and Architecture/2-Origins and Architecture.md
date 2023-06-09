# 可编程逻辑器件的发展简史
+ 1956 PROM (Programmable Read Only Memory)
+ 1971 EPROMs (Eraseable Programmable Read-only Memory)
+ 1975 PLAs (Programmable Logic Arrays)
+ 1978 PALs (Programmable Array Logic) <br>
## 不同点
+ PROM: 或门/总项可编程(改变存储器内容)，与门/乘积项固定(地址解码逻辑)
+ CPLD: 主要结构是宏单元，每个宏单元由多个PAL结构的电路块构成，具有注册输出和互连的可编程结构
+ PAL: 可编程的与阵列+固定或阵列。采用熔丝编程，比PLA灵活快速
+ PLA: 可编程的与阵列+可编程的或阵列
+ FPGA: 主要结构是查找表，内部主要由大量纵横排列的逻辑块构成，大量的逻辑块通过内部连线和开关就可以实现非常复杂的逻辑结构
<br>
## FPGA简要历史
+ FPGA产业萌芽于可编程只读存储器（PROM）和其他可编程逻辑器件（PLD）
+ 1983 Altera公司成立
+ 1984 交付了业界第一个可重复编程的逻辑器件——EP300: 包装中有一个石英窗，允许用户用紫外线灯照射染料，以擦除保存器件配置的EPROM单元
+ 1985 Xilinx发明了第一个商业上可行的填充式可编程门阵列——XC2064: 有可编程的门，门之间有可编程的互连，有64个可配置逻辑块CLBs、两个三输入查找表LUTS
+ 20世纪90年代初，FPGA主要用于电信和网络
+ 20世纪90年代末，FPGA进入了消费者、汽车和工业应用<br>

## 小结
+ FPGA只由三个元素组成: 一条线、一个门和一个寄存器或触发器。创建互连模式是FPGA设计的核心
+ PLD是所有逻辑器件的一个子集，FPGA是PLD的一个子集。标准逻辑的范围更广，它包括额外的TTL系列如LVTTL，额外的CMOS系列如HC，LVC和biCMOS，BCT，HCT等，以及差分逻辑系列如ECL和LVDS<br>
+ 标准逻辑、可编程逻辑、全定制器件也被称为通用集成电路。在ASIC和全定制之间的是现在被称为ASSP的器件
+ FPGA与特定应用集成电路ASIC和特定应用标准产品ASSP竞争，在许多应用中成功取代了它们，当涉及到数字设备时，FPGA似乎是未来的趋势
+ 芯片是由门和触发器的阵列组成的，导线可以将它们按模式连接在一起，这些模式为更大的功能创造了逻辑，如计数器、计时器、状态机、ALU，甚至整个CPU<br>

**现场可编程门阵列（FPGA）是由门、寄存器和路由线组成的可编程逻辑器件，以一种模式连接在一起，可以在器件部署后进行编程**
<br><br>
# CPLD发展历史
+ CPLD是在CMOS中建立的，可以重新编程，区别于双极PAL
+ 定义互连和CPLD的程序被存储在片上EE提示中，Altera扩展了该概念：将多个PAL结构称为宏单元放入一个单一的集成电路封装中，其中所有的输入引脚对每个宏单元都可用，任何输出引脚都可以由任何宏单元驱动，然后可以反馈给输入阵列
+ 复杂可编程逻辑器件CPLD是FPGA的前身，其顶层结构是用互连线连接的PAL宏单元
+ CPLD本质上是分层的设备，层次结构从许多较小的逻辑功能中创造出较大的逻辑系统: 由更大的电路组组成的(LABs)——由16个宏单元组成的逻辑阵列块，宏单元之间有局部路由。可编程互联器阵列(PIA)——将宏单元连接在一起的互连线矩阵，将单元的输出输送到其他单元的输入，实验室之间的路由网络，该结构很适合需要每个触发器都有大量逻辑的问题，如复杂的16个状态的状态机或宽输入解码器

## 限制与优势
+ 容易生成宽泛的输入函数
+ 容易计算出非常可预测的时序
+ 胶合逻辑应用的好选择
* 限制: 对于需要大量的寄存器、数据传输、总线接口的设计，这些逻辑密集型触发器匮乏的设备不能很好地扩展，导致了另一种PLD架构的发展，即FPGA。
## 小结
+ CPLD为可编程逻辑器件重新引入了**可重编程性**
+ CPLD加强了分层设计的方法
+ CPLD的结构允许轻松设计宽输入的组合逻辑功能，如地址解码器和具有确定时间的状态机
+ 对于需要许多翻转的设计来说，CPLD的结构并不能有效地扩展，这已经成为FPGA的范畴
<br><br>
# LUTS和FPGA架构。
发明FPGA是为了提供一种具有极大灵活性和效用的通用数字逻辑设备。
## FPGA的发展与结构的演变
+ 1955 Xilinx制造了具有N x N阵列单元的FPGA，其全局路由沿着中心脊柱进行
+ 2005 乘法器与硬核处理器一起被添加进来，在这种情况下，是一台功率PC
+ 2007 增加了DSP内核<br>
从这一演变中可以看出，FPGA不再是在胶合逻辑的领域中运作，而是正在成为子系统或完整的系统本身。这种发展在一定程度上是由路由开关使用SRAM存储器所推动的，它比EEPROM具有更高的密度。另一个发展是使用布尔表达式以外的新的设计输入方法，包括原理图输入和HDL语言，如Verilog和VHDL。
## 基本逻辑单元是如何使用查找表LUTS工作的
+ 为创造一个更灵活的通用逻辑设备，FPGA首先被设计成模仿门阵列。然而在许多情况下，逻辑不是用晶体管门实现的，而是由存储器实现的
+ 第一批FPGA是一个由三个输入查找表LUTS组成的逻辑单元阵列。FPGA的结构与CPLD不同，因为逻辑单元更小，通常以LUT的形式实现
+ FPGA中的路由是分层次的：在最底层有路由开关，由SRAM的一个位，或闪存的一个位，或一个保险丝控制。在本地路由中有许多路由开关，用于连接各种逻辑元素或块。
+ FPGA是由逻辑块的海洋组成的。块组由长线或非常长的线连接。像时钟这样的普通信号在被称为全球网络的特殊路由网络上进行路由。
## 路由如何成为影响性能的更大因素
用于创建路由开关的配置存储器的类型，是决定FPGA性能和能力差异的最重要方面。<br>
+ 抗蚀剂FPGA以其可靠性而闻名，但它们是一次性可编程的，而且价格昂贵。
+ FLASH FPGA也是非常可靠的，也有可重复编程的，但价格比SRAM FPGA高。
+ SRAM FPGA是可编程的，具有最高密度和最低成本的同等逻辑。<br>
四个主要的PLD供应商有各种产品，包括许多配置类型。
- Xilinx提供FLASH CPLD和FPGA以及SRAM FPGA
- Altera提供FLASH CPLD和SRAM FPGA。
- 莱迪思销售SRAM CPLD和FPGA
- Microsemi提供Antifuse和FLASH FPGA。
### 为什么要使用CPLD而不是FPGA？
CPLD可能是一个更便宜的选择，它也可能允许在相同的空间里有更多的IO，而且逻辑成本更低。如果你必须满足非常严格和确定的时间要求，CPLD也可能是最佳选择。
### FPGA设计流程
- 从设计输入开始，继续进行仿真以验证逻辑是否按照预期实现
- 然后，工具将进行综合，也称为映射，将逻辑映射到设备架构上。
- 接下来，该工具将通过放置和路由或拟合设计来创建单元之间的互连。在拟合完成后，再运行一次仿真是很好的做法。
- 下一步就是使用该工具创建一个编程文件，然后将其下载到FPGA器件中进行测试。<br>
## 比较FPGA与CPLD
+ FPGA是高度灵活的通用数字逻辑器件，部分原因是巧妙地使用存储器元件作为基本逻辑单元的LUTS。
+ FPGA的扩展性比CPLD好。为大型设计和需要许多触发器的设计创造更低成本的解决方案。因为FPGA的结构比CPLD的颗粒更细，所以路由对性能的影响更大。
+ FPGA配置存储器可以使用几种不同的技术之一来实现，包括SRAM、Flash和Antifuse，这种选择会影响成本和性能。
+ FPGA提供了无数的方法来创建您的下一个逻辑设计。
