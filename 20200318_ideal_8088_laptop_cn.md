# 打造理想中的笔记本电脑第一话（8088 & IBM PC）

Originally posted at March 18, 2020: [https://www.mydigit.cn/thread-133380-1-1.html](https://www.mydigit.cn/thread-133380-1-1.html)

没想到发帖时已经是3月中旬了，这台笔记本是从1月中旬开始计划的，两个月时间转眼就过去:sweat:。不过疫情还没结束，还有时间继续研究。上次做了一张IBM XT的mini卡片电脑。原本就是计划用在笔记本上的，只是工作也比较繁忙就一直搁置，现在算是又走出了一步吧。

![img0](images/20200318_00.jpg) 

这次要做的就是一台兼容IBM PC的笔记本。

## 【配置介绍】
CPU：8088（NEC V20）
内存：640KB
硬盘：可选CF卡/DiskOnChip 作为存储设备
显示：1024x768 TFT（led背光）/显卡兼容CGA/VGA
外设：软驱，串口，键盘，标准ISA扩展
系统：DOS6.22

## 【准备工作】

首先配置方案我们已经确定，接下来就是外壳，外壳我考虑过几种，第一是亚克力，第二是铝合金CNC加工，第三是借用其他笔记本外壳，第四是开模注塑。综合考虑后还是选择第三种，说不定后面还要改动。

成品笔记本型号众多，但是锁定几个固定条件后也好选择
1，厚度要厚（古董元件高度较高，而且还要做叠层电路板）
2，尽量不要改造（那么尽量要有原装软驱位）
3，外壳存世量比较多，这也就是说生产时间要接近现在的
4，外观，个人喜欢那种前后厚度一致的，就是不收边的，比较方正，棱角分明。

其实锁定了有软驱位，生产时间又要靠近现在的，范围就缩小了，DELL，HP，富士通这些商务本一般都带软驱。不过我检索的时候偶然看到一台东芝J60，这台机用的酷睿双核的U，竟然还带软驱，厚度巨厚，所以基本条件都符合了，就选择它。
TOSHIBA J60就是这个样子：

![img1](images/20200318_01.jpg) 

既然已经选定好了外壳，接下来就是做些准备工作
1，更改液晶背光
2，制作LVDS屏线
3，外壳小改动
4，测绘内部空间，孔位，确定主板大小。

第一步：改造液晶背光，我测试过原版的液晶背光，就背光就需要1A的电流！我估计我整个系统都要不了1A，所以必须改造

![img2](images/20200318_02.jpg) 

选用5V供电的LED驱动板，不是很好找，不过还是有售

![img3](images/20200318_03.jpg) 

改造的过程没有详细拍图了，因为主要是制作古董电脑，重点就不放在这里啦。经过测试，这条LED背光需要0.5A的电流，已经小了一半，但还是感觉高了。
点亮屏幕后才发现这个亮度实在太高了，高到白天都有点刺眼，所以又调整了驱动板的反馈电阻，把背光调到最低都觉得很亮。
所以，再测试电流发现电流只需要0.1A了！就是100ma就可以达到比原版1A电流的亮度还高。所以这个改造很有必要，对以后续航也是很大帮助。

![img4](images/20200318_04.jpg) 

改造完后开始测试啦，由于摄像头对光线比较敏感，实际亮度比图高很多（这是100ma电流的情况下）。

第二步，制作LVDS屏线。
查询这张屏是30P 单6的LVDS屏，所以买了一条屏线，用屏蔽胶处理一下，屏线基本就搞好了。

![img5](images/20200318_05.jpg) 

第三步，外壳改动主要是去除掉一下原本不要的支撑点。然后还要装个小液晶屏用于显示电流，键盘状态。先测绘好液晶屏需要的轮廓，用电钻先挖个大概。

![img6](images/20200318_06.jpg) 

![img7](images/20200318_07.jpg) 

然后。。。 用美工刀一点点削。不管怎么说，除了被我划了一下，其他都非常完美，严丝合缝。

![img8](images/20200318_08.jpg) 

![img9](images/20200318_09.jpg) 

第四步，测绘图纸，主板轮廓和孔所在位置需要确定下，这样PCB板的大小就确定好了。

原主板：

![img10](images/20200318_10.jpg) 

测绘的孔位关系：

![img11](images/20200318_11.jpg) 

## 【主板制作】

准备工作做好了，现在就是根据之前提出的配置要求开始设计主板。

1，绘制主板/显卡LVDS驱动
主板电源部分，每一路电源都有电流检测。方便测试功耗

![img12](images/20200318_12.jpg) 
IO译码和UART

![img13](images/20200318_13.png) 
FDC

![img14](images/20200318_14.png) 

其他部分图纸太多，统一放到附件中算了。大家可以下载做个参考。

2，绘制PCB。布线真的是头大，好在这块板足够大，随意布线都可以。

![img15](images/20200318_15.jpg) 

3D预览，渲染库不全

![img16](images/20200318_16.jpg) 

等了5天，板子终于回来了。迫不及待开始焊接。

先焊接显卡吧：

![img17](images/20200318_17.jpg) 

背面再来一张

![img18](images/20200318_18.jpg) 

主板焊接：

![img19](images/20200318_19.jpg) 

放大镜下面看焊盘有没有虚焊：

![img20](images/20200318_20.jpg) 

这里出现了整个工程中最悲催的事情，我焊接了6个小时，结果不能运行，我又花了两个小时把焊好的元件一个个拆下来除错。关键是还没找到问题。此时已是深夜，只能到第二天试试。

第二天实在没办法，只能截断全部线路，用最小系统法慢慢排除。最后找到问题是CPU接口镜像了。又得重新做一款板子了。
新的板子颜色也改下好了。又等了4天，又可以开始愉快的焊接了。

![img21](images/20200318_21.jpg) 

CPU板用的去年做的那款，非常稳定：

![img22](images/20200318_22.jpg) 

焊接完成大概就是酱紫的啦，装上模块后介绍一下。虽然板子看起来很空旷，但是用的是ISA总线，上面还可以装很多其他模块的。

![img23](images/20200318_23.jpg) 

![img24](images/20200318_24.jpg) 

电源部分，键盘IO部分：

![img25](images/20200318_25.jpg) 

电池：

![img26](images/20200318_26.jpg) 

外部ISA接口：

![img27](images/20200318_27.jpg) 

CF卡和软驱:

![img28](images/20200318_28.jpg) 

整个工程差不多手工部分就结束了：

![img29](images/20200318_29.jpg) 

键盘也重新买了张英文版的新键盘：

![img30](images/20200318_30.jpg) 

两台对比一下：

![img31](images/20200318_31.jpg) 

然后上电，开机！ 这里是从CF卡进的系统，装的dos6.22
BIOS是用的开源的bios，减少了很多工作量。

![img32](images/20200318_32.jpg) 

小液晶屏主要是后面协助我做键盘扫描程序，因为键盘驱动还没有写完。另外液晶屏后面主要显示电池续航，整机功耗等。

![img33](images/20200318_33.jpg) 

由于此贴主要是制作过程，所以测试和使用的话我打算后面另外再写一篇专门的介绍。
附上图纸，大家可以参考。BIOS在上一篇帖子中已经上传，没有改过的。

[图纸.rar (72.84 KB)](https://9game.oss-us-west-1.aliyuncs.com/book8088stories/files/20200318_blueprint.rar)

发帖时距离制作完成也有几天了，此时我已经开始制作一款7寸的便携式笔记本。集成度相对高些，但是也更稳定。其实我也不止研究8088古董，我平时喜欢DIY笔记本，915PM , 945PM , PM965 , PM45 这几个独显平台都在DIY范围，就是画图时间实在太长，如果有喜欢DIY的朋友我们可以一起研究。

全文完