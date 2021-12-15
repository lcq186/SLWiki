### 三安智能BIN CSV文档

客户文档

[MES导出文档](C:\Users\lcq18\Desktop\FT35-20-SCM35BUC00E1Z2-FFN2001-009-MP.xls)

##### 需求根据客户要求 

使用MES导出文档生成Bin条件,并重新排序分Bin优先级顺序.

导出文档说明

![image-20211019134927493](https://lcq186-1256847298.cos.ap-nanjing.myqcloud.com/img/image-20211019134927493.png)

header固定2行 第一列 属于MES导出的Bin序号,第二列Bin名称

项目分割 如: VF1_Min  使用"_"进行分割前缀属于项目名称,导入时候用于识别项目名称,后缀是等级上下限值标识.

BinSpec 对应Bin名称.

表格内容说明,如C,D 列 是VF1的所有分Bin 条件, -99999.00 _+99999.00 属于没有添加条件,5-5.5 属于等级条件上下限,这个范围必须在项目等级存在.

##### NG 设置

  OUTBIN 属于NGbin项目

  OPEN,SHORT ,开路,短路,在vb 上是需要客户添加一个小电流VF 小电流并设置为OS 项目名称,作为导入条件









​	



