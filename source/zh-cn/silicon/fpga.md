---
title: FPGA
---

FPGA（Field Programmable Gate Array）是在PAL、GAL、EPLD、CPLD等可编程器件的基础上进一步发展的产物，作为ASIC领域中的一种半定制电路而出现的，即解决了定制电路的不足，又克服了原有可编程器件门电路有限的缺点。现归属于PLD类器件，主要“活跃”于通信领域。

由于FPGA需要被反复烧写，它实现组合逻辑的基本结构不可能像ASIC那样通过固定的与非门来完成，而只能采用一种易于反复配置的结构。查找表 LUT（Look-Up-Table）可以很好地满足这一要求，目前主流FPGA都采用了基于SRAM工艺的查找表结构，也有一些军品和宇航级FPGA采用Flash或者熔丝与反熔丝工艺的查找表结构。通过烧写文件改变查找表内容的方法来实现对FPGA的重复配置。 

FPGA市场占有率最高的两大公司Xilinx和Altera生产的FPGA都是基于SRAM工艺的，需要在使用时外接一个片外存储器以保存程序。上电时，FPGA将外部存储器中的数据读入片内RAM，完成配置后进入工作状态；掉电后FPGA恢复为白片，内部逻辑消失。这样FPGA不仅能反复使用，还无需专门的FPGA编程器，只需通用的EPROM、PROM编程器即可。

## PLD

可编程逻辑器件PLD (programmable logic device) ，逻辑功能按照用户对器件编程来确定，集成度很高，PLD能完成任何数字器件的功能，上至高性能CPU，下至简单的74电路，都可以用PLD来实现。

20世纪70年代，最早的PLD诞生，现场可编程逻辑器件（FPLD）其中应用最广泛的当属现场可编程门阵列（FPGA）和复杂可编程逻辑器件（CPLD）。

### CPLD

复杂可编程逻辑器件 CPLD(Complex Programmable Logic Device)，是从PAL和GAL器件发展出来的器件，其规模大，结构复杂，属于大规模集成电路范围。

CPLD主要是由可编程逻辑宏单元（LMC，Logic Macro Cell）围绕中心的可编程互连矩阵单元组成，其中LMC逻辑结构较复杂，并具有复杂的I/O单元互连结构，可由用户根据需要生成特定的电路结构，完成一定的功能。由于 CPLD内部采用固定长度的金属线进行各逻辑块的互连，所以设计的逻辑电路具有时间可预测性，避免了分段式互连结构时序不完全预测的缺点。到90年代，CPLD发展更为迅速，不仅具有电擦除特性，而且出现了边缘扫描及在线可编程等高级特性。较常用的有Xilinx公司的EPLD和Altera公司的CPLD。


### FPGA

FPGA是现场可编程门阵列（Field Programable Gate Array）的简称，两者的功能基本相同，只是实现原理略有不同。

FPGA通常包含三类可编程资源：可编程逻辑功能块、可编程I/O块和可编程互连。可编程逻辑功能块是实现用户功能的基本单元，它们通常排列成一个阵列，散布于整个芯片；可编程I/O块完成芯片上逻辑与外部封装脚的接口，常围绕着阵列排列于芯片四周；可编程内部互连包括各种长度的连线线段和一些可编程连接开关，它们将各个可编程逻辑块或I/O块连接起来，FPGA在可编程逻辑块的规模，内部互连线的结构和采用的可编程元件上存在较大的差异。较常用的有Altera、Xinlinx和Actel公司的FPGA。FPGA一 般用于逻辑仿真。电路设计工程师设计一个电路首先要确定线路，然后进行软件模拟及优化，以确认所设计电路的功能及性能。然而随着电路规模的不断增大，工作 频率的不断提高，将会给电路引入许多分布参数的影响，而这些影响用软件模拟的方法较难反映出来，所以有必要做硬件仿真。FPGA就可以实现硬件仿真以做成模型机。将软件模拟后的线路经一定处理后下载到FPGA，就可容易地得到一个模型机，从该模型机，设计者就很直观地测试其逻辑功能及性能指标。

ASIC芯片内部架构较为简单，不可以硬件编程，只能用来专门处理某一种功能，灵活性最差，但是在执行某一种任务上的效率最高。ASIC也被称为专用集成电路。

### FPGA VS CPLD

CPLD的程序是固化在内部flash的，掉电之后重新上电程序依然在。而FPGA内部并没有flash，掉电之后程序会消失，当然可以外部挂一个flash存储程序，每次掉电重启都从flash加载。

#### 通常分类方法

* 将以乘积项结构方式构成逻辑行为的器件称为CPLD，如Lattice的ispLSI系列、Xilinx的XC9500系列、Altera的MAX7000S系列和Lattice(原Vantis)的Mach系列等。
* 将以查表法结构方式构成逻辑行为的器件称为FPGA，如Xilinx的SPARTAN系列、Altera的FLEX10K或ACEX1K系列等。
* 尽管FPGA和CPLD都是可编程ASIC器件，有很多共同特点，但由于CPLD和FPGA结构上的差异，具有各自的特点:
* CPLD更适合完成各种算法和组合逻辑，FPGA更适合于完成时序逻辑。换句话说，FPGA更适合于触发器丰富的结构，而CPLD更适合于触发器有限而乘积项丰富的结构。
* CPLD的连续式布线结构决定了它的时序延迟是均匀的和可预测的，而FPGA的分段式布线结构决定了其延迟的不可预测性。
* 在编程上FPGA比CPLD具有更大的灵活性。CPLD通过修改具有固定内连电路的逻辑功能来编程，FPGA主要通过改变内部连线的布线来编程；FPGA可在逻辑门下编程，而CPLD是在逻辑块下编程。
* FPGA的集成度比CPLD高，具有更复杂的布线结构和逻辑实现。
* CPLD比FPGA使用起来更方便。CPLD的编程采用E2PROM或FASTFLASH技术，无需外部存储器芯片，使用简单。而FPGA的编程信息需存放在外部存储器上，使用方法复杂。
* CPLD的速度比FPGA快，并且具有较大的时间可预测性。这是由于FPGA是门级编程，并且CLB之间采用分布式互联，而CPLD是逻辑块级编程，并且其逻辑块之间的互联是集总式的。
* 在编程方式上，CPLD主要是基于E2PROM或FLASH存储器编程，编程次数可达1万次，优点是系统断电时编程信息也不丢失。CPLD又可分为在编程器上编程和在系统编程两类。FPGA大部分是基于SRAM编程，编程信息在系统断电时丢失，每次上电时，需从器件外部将编程数据重新写入SRAM中。其优点是可以编程任意次，可在工作中快速编程，从而实现板级和系统级的动态配置。
* CPLD保密性好，FPGA保密性差。
* 一般情况下，CPLD的功耗要比FPGA大，且集成度越高越明显。

---

## 芯产品

### Anlogic

#### EG4S20 FPGA

荔枝糖使用安路科技(Anlogic Technologies) 的EG4S20作为核心单元, 20K逻辑单元(LUT4/LUT5混合架构)，约130KB SRAM，内置32bit位宽64MBit SDRAM，丰富的LVDS引脚，内置12-bit 1MSPS ADC ，FPGA可以模拟“HummingbirdE200/E203 RISC-V软核

### Gaoyun LittleBee

#### GW1N-1  FPGA

GW1N-LV1QN48C6/I5, equipped with 1152 LUT4 logic resources, 1 PLL and 4 Block total 72Kbit SRAM,