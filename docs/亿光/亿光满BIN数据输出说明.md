## 亿光满BIN 数据输出说明

##### 原始需求:

![image-20211021165227594](https://lcq186-1256847298.cos.ap-nanjing.myqcloud.com/img/image-20211021165227594.png)

经过现场测试. LAMP机台串口信号

##### 波特率:2400 数据位:8 停止位:1 校验:None

机台满BIN数据会重复发送3次 调试时需要重复发送3次命令, 如果3次不连续将重新计次.

<img src="https://lcq186-1256847298.cos.ap-nanjing.myqcloud.com/img/image-20211021165704447.png" alt="image-20211021165704447" style="zoom: 50%;" />









##### 安装后需要配置通用功能勾选项目,并设置输出目录保存,确定.

系统设置  定制功能设置-打印模板列表选着-亿光文件输出.

![image-20211021172838016](https://lcq186-1256847298.cos.ap-nanjing.myqcloud.com/img/image-20211021172838016.png)



<img src="https://lcq186-1256847298.cos.ap-nanjing.myqcloud.com/img/image-20211021170325404.png" alt="image-20211021170325404" style="zoom: 67%;" /><img src="https://lcq186-1256847298.cos.ap-nanjing.myqcloud.com/img/image-20211021170500809.png" alt="image-20211021170500809" style="zoom: 67%;" />

##### 串口通讯协议设置

#####  ![image-20211022213213590](https://lcq186-1256847298.cos.ap-nanjing.myqcloud.com/img/image-20211022213213590.png)





##### 料号及其他信息设置

![image-20211021170631902](https://lcq186-1256847298.cos.ap-nanjing.myqcloud.com/img/image-20211021170631902.png)

##### 输出样式

###### 存放路径：   D:\op\Sato_EverLight.txt

######  ![image-20211021171550604](https://lcq186-1256847298.cos.ap-nanjing.myqcloud.com/img/image-20211021171550604.png)

## 2021.10.25 需求更新

等级输出定义


第一个项目为亮度或光电流，具体项目是iv,lm,if,ir;

第二个项目为饱和电压，具体项目为vf，或VR；

第三个为波长项目，具体项目为wld或cie_xy

等级重新组合方式使用 |分割空值保留|符号;

添加几种名称设置, 输出机器号改机种名称

## 2021.10.26 需求更新

 客户等级mark 有需要输出有不需要输出.

临时方案: 用户手动关闭或打开来控制文件输出等级名称

<img src="https://lcq186-1256847298.cos.ap-nanjing.myqcloud.com/img/image-20211026142907055.png" alt="image-20211026142907055" style="zoom: 67%;" />

## 2021.10.27 需求更新

等级输出重新定义

第一个项目为亮度或光电流，具体项目是iv,lm,if,ir;

第二个为波长项目，具体项目为wld或cie_xy

第三个项目为饱和电压，具体项目为vf，或VR；

文件输出时NgBin由于没有等级,使用Bin名称输出到等级第一个分割项内,其他项为空 .  <font Color="FF00">   (在不启用 使用空白等级输出 生效).</font>







