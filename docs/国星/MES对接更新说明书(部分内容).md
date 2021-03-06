### MES 对接更新说明书(部分内容)

[需求文档]()

版本履历

| 版本   | 更新内容                                                  | 日期       | 其他 |
| ------ | --------------------------------------------------------- | ---------- | ---- |
| V1.0.0 | 输出测试数据文档保存格式更改 UTF-8,锁定写入.              | 2021.09.22 |      |
|        | 原有分割与现功能不符,更新分割功能.                        | 2021.09.22 |      |
|        | 添加固定资产号设置                                        | 2021.09.22 |      |
|        | 文件命名  $"{Lot}\_{固定资产号}\_{工单号}\_{时间戳]}.csv" | 2021.09.22 |      |
| v1.0.1 | 设定时间,Bin文件导出                                      | 2021.09.24 |      |
|        | 由于原系统界面排版问题,顾添加一个控件形式界面             | 2021.09.24 |      |
| v2.0.0 | 前版本所有更新合并到等级卡控版本                          | 2021.09.26 |      |
|        | 资产号编辑位置修改                                        | 2021.09.26 |      |
| V2.1.1 | MES 机器统一使用10位Mark                                  | 2021.10.14 |      |
|        | 测试数据备份导出                                          | 2021.10.14 |      |
|        | Bin文件导出 修改为JSON 导出                               | 2021.10.14 |      |
|        | 添加点检模式 测试数据导出                                 | 2021.10.14 |      |
| V2.1.2 | 添加业务流程                                              | 2021.10.22 |      |
|        | 数据文件和bin 文件修订                                    | 2021.10.22 |      |
| V2.1.3 | 添加webAPI接口                                            | 2021.10.25 |      |
|        | 输出csv数据文件名 前缀改固定"LOT" 字符串                  | 2021.10.26 |      |

# 更新说明

## V1.0.0  2021.09.22

##### 1.1	 批量开始必须设置资产号:

![image-20210922103814749](https://lcq186-1256847298.cos.ap-nanjing.myqcloud.com/img/image-20210922103814749.png)

 系统设置->数据保存设定->资产号->修改后确定保存  输入值:不能为空白或"资产号"形式,否则无法批量开始

![image-20210922104157461](https://lcq186-1256847298.cos.ap-nanjing.myqcloud.com/img/image-20210922104157461.png)

##### 1.2 测试数据分割设置

![image-20210922104408446](https://lcq186-1256847298.cos.ap-nanjing.myqcloud.com/img/image-20210922104408446.png)

##### 1.3 写数据文档到达设定行重新创建文档

​	批量开始,测试数据到达设定行将根据文件命名方式创新创建文档写入.

​	重新批量开始 ,行计数重新开始,数据列 [No.] 由计数器清零控制.

#### ![image-20210922143804541](https://lcq186-1256847298.cos.ap-nanjing.myqcloud.com/img/image-20210922143804541.png)

##### 1.4	设定时间,Bin文件导出

系统设置 -> 修改首次导出时间和间隔时间(设置0不导出Bin条件)并设置路径

<Font color=FF00>保存路径必须存在否则会保存异常</font>

![image-20210924170725966](https://lcq186-1256847298.cos.ap-nanjing.myqcloud.com/img/image-20210924170725966.png)

![image-20210926143906036](https://lcq186-1256847298.cos.ap-nanjing.myqcloud.com/img/image-20210926143906036.png)

## V2.1.1   2021.10.14

<img src="C:/Users/lcq18/AppData/Roaming/Typora/typora-user-images/image-20211014154738048.png" alt="image-20211014154738048" style="zoom:67%;" />

1. 由于mes 提取数据文件 单独文件没有子目录模式,所有添加批量结束导出csv

2. 点检校正数据输出, 在点检或校正测试结束后输出到指定文件夹下.

## V2.1.2   2021.10.22

![image-20211022134808189](https://lcq186-1256847298.cos.ap-nanjing.myqcloud.com/img/image-20211022134808189.png)

 操作员量产测试  信息修改和文件设定需要 管理员密码 对应 工单号编辑和计数清零和工程模式, 




~~~![image-20211022135108856](https://lcq186-1256847298.cos.ap-nanjing.myqcloud.com/img/image-20211022135108856.png)~~~
~~~

批量开始 需要输入工单号 获取服务器数据 (目前没有mes 接口 方式和文档临时跳过此功能) 

提示 检查 补偿系数, 点检测试流程,并提示信息.

![image-20211022135406745](https://lcq186-1256847298.cos.ap-nanjing.myqcloud.com/img/image-20211022135406745.png)

## V2.1.3  添加webAPI接口

安装后设置  webAPI  服务器地址

使用管理员密码修改机器号, 重启软件自动获取 工单号,批量号显示在基本信息

![image-20211025164536569](https://lcq186-1256847298.cos.ap-nanjing.myqcloud.com/img/image-20211025164536569.png)

 

​		

   





