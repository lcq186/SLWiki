---
苏州索拉科技
---

## 光宝 OSD Tester AOI 通讯协议定制版 1.2

| V1.0 | 初始版本 OSD Tester AOI数据 |      |                                |
| ---- | --------------------------- | ---- | ------------------------------ |
| V1.2 | 业务流程说明                    | 2020-12-16   | CQ.LI |
| v1.3 | 客户版本为1.3 | 2021.06.01 | CQ.LI |
<div style="page-break-after: always;"></div>
### 1.登入接口 

##### 1.1 接口说明

| 概述     | 登入接口                            |                  |
| -------- | ----------------------------------- | ---------------- |
| 调用方法 | /MachineServiceHttp/OPR/CommonLogin |                  |
| 测试环境 | /MachineServiceTest/OPR/CommonLogin | 能否提供外网接口 |
| 请求方式 | POST                                | json             |

##### 1.2 请求说明

| 参数名称 | 是否必须 | 类型   | 描述                                  |
| -------- | -------- | ------ | ------------------------------------- |
| Username | 必须     | string | 用戶名為MES系統登錄用戶名             |
| Password | 必选     | String | 密碼採用DES加密傳輸                   |
| Device   | 必选     | String | 設備名稱                              |
| Language | 必选     | String | 简体中文：CN，英文：EN  ,繁体中文：TW |

##### 1.3 请求 

```json
{
  "UserName": "CQ.li",
  "Password": "****",
  "Device": "AT01",
  "Language": "CN"
}
```
~~~c#
public class LoginInfo
{ 
    public string UserName { get; set;}
    public string Password { get; set;}
    public string Device { get; set;}
    public string Language { get; set;}
}
~~~

<div style="page-break-after: always;"></div>





##### 1.4 返回说明

| 参数名称 | 类型   | 描述     |
| -------- | ------ | -------- |
| data     | Object | 返回数据 |
| Token    | String | 令牌     |

###### 1.4.1 返回成功

~~~ json
{
    "success":1,
    "data":{
        "Token":"xxxxxxx"
    }
}
~~~

```c#
public class Root
{  
    public int success { get; set; }
    public Data data { get; set; }
}
public class Data
{
    public string Token { get; set; }
}

```

###### 1.4.1 返回错误

~~~json
{
"success":0,
"errorno":"错误代码",
"errormsg":"错误原因"
}
~~~

~~~C#
public class Root
{
    public int success { get; set; }
    public string errorno { get; set; }
    public string errormsg { get; set; }
}
~~~

<div style="page-break-after: always;"></div>



### 2.SMD AOI接口

##### 2.1   接口说明

| 接口概述  | SMD AOI接口                                            |        |
| --------- | ------------------------------------------------------ | ------ |
| 调用方式  | /MachineServiceHttp/Machine/GetTesterDataForPowerBI_OK | GO-BIN |
| 測試環境: | /MachineServiceTest/Machine/GetTesterDataForPowerBI_OK |        |
|           | /MachineServiceTest/Machine/GetTesterDataForPowerBI_NG | NG-BIN |
|           | /MachineServiceTest/Machine/GetTesterDataForPowerBI_NG |        |
| 请求方式  | POST                                                   |        |

##### 2.2   请求说明

| 参数名称        | 是否  必须 | 类型   | 描述                                   |
| --------------- | ---------- | ------ | -------------------------------------- |
| Token           | 必选       | String | 令牌，登录时获得                       |
| Language        | 必选       | String | 简体中文：CN，英文：EN ,繁体中文：TW   |
| VENDORCODE      | 必选       | String | 厂商代码，针对不同厂商会读取不同规格档 |
| LOTNO           | 必选       | String | 批号                                   |
| PRODUCTID       | 必选       | String | 机种                                   |
| EQPNAME         | 必选       | String | 机台号                                 |
| EQPTYPE         | 必选       | String | 机台类型                               |
| COMMENT         | 必选       | String | 备注                                   |
| QUANTITY        | 必选       | String | 测试数量                               |
| PRODUCTLINECODE | 必选       | String | 线别                                   |
| STEPNAME        | 必选       | String | 测试站站别                             |
| REASON          | 必选       | Object | 测试异常项目明细                       |

###### 2.2.1 內容

| 参数名称 | 是否必须 | 类型   | 描述     |
| -------- | -------- | ------ | -------- |
| TESTERNO | 必选     | String | 测试箱号 |
| REASON   | 必选     | String | 不良项目 |
| LOSSES   | 必选     | String | 不良数量 |

<div style="page-break-after: always;"></div>
##### 2.3 请求说明

~~~JSON	
{
    "Token":"132456789009876543",
    "Language":"EN",
	"VENDORCODE":"109912",
    "LOTNO":"2013011234",
    "PRODUCTID":"LTST-19278",
    "EQPNAME":"22T101",
    "EQPTYPE":"TESTER",
    "COMMENT":"Description",
    "QUANTITY":"100",
    "PRODUCTLINECODE":"22",
    "STEPNAME":"2213101-2301",
    "REASON ":[
        {
            "TESTERNO":"测试箱号",
            "REASON":"不良项目",
            "LOSSES":"不良数量"
        },
        {
            "TESTERNO":"测试箱号",
            "REASON":"不良项目",
            "LOSSES":"不良数量"
        }
    ]
}
~~~

~~~c#

public class Item
{  
    public string TESTERNO { get; set; }   
    public string REASON { get; set; }
    public string LOSSES { get; set; }
}
 
public class Root
{  
    public string Token { get; set; }
    public string Language { get; set; }
    public string VENDORCODE { get; set; }
    public string LOTNO { get; set; }
    public string PRODUCTID { get; set; }
    public string EQPNAME { get; set; }  
    public string EQPTYPE { get; set; } 
    public string COMMENT { get; set; }  
    public string QUANTITY { get; set; } 
    public string PRODUCTLINECODE { get; set; } 
    public string STEPNAME { get; set; } 
    public List<Item> REASON { get; set; }// Item[512];
}
~~~

##### 2.4 返回说明

| 参数名称 | 类型   | 描述                      |
| -------- | ------ | ------------------------- |
| data     | Object | 返回数据                  |
| success  | String | 1:成功，0:错误            |
| errorno  | int    | 错误代码 (发生错误时才有) |
| errormsg | String | 错误信息 (发生错误时才有) |
|          |        |                           |

###### 2.4.1返回成功

~~~JSON	
{
    "success":1
}
~~~

###### 2.4.2返回错误

~~~JSON	
{
    "success":0,
    "errorno":错误代码,
    "errormsg":错误原因,
}
~~~

#### 3.业务流程说明

  ###### 3.1 登入流程

~~~mermaid
graph LR
  Start[用户登入] --> Login[登录请求]  
  Login-->Input[输入密码]
  Input-->Condition{获取令牌} 
  Condition--Yes-->Token[获取令牌]
  Condition--No-->Login  
~~~



###### 3.3  上传流程方案2

~~~mermaid
graph LR
SolarTester([测试仪软件启动界面])-->InputInfo{输入信息}
InputInfo--Yes-->LotStart[批量测试]
LotStart -->LotEnd[批量结束]
LotStart-->LotErr[批量异常结束]
LotEnd-->Post[POST]
Post-->PostErr[Err错误提示] 
LoadFile[加载文件]-.->InputInfo
Token[令牌]-.->InputInfo
Post--成功-->ClearAllBin((清除软计数Bin))
PostErr-->Default([默认界面])
ClearAllBin-->Default 
LotErr-->Default

~~~



#### 未确认事项

​    令牌是否有超时时间?

​    上传时机,[批量结束],[结束lot],进行上传 ?

​    重复数据发送是否有影响?

​    结束批量并不会清空Bin桶数量信息,结束批量上传后是否清空软件计数?

​    能否提供外网测试接口 ?

​    不良BIN判断定义方式？





# 1.0 OKBin 数据推送

### 1.1.0接口简介： 

  批量结束收推送 OKBin 信息

| 基本信息： |                      |
| ---------- | -------------------- |
| 接口地址   | /apigateway/api/home |
| 请求类型   | POST                 |
| APPID      |                      |
| 鉴权方式   |                      |



### 1.2.0 主体

| **名称**            | **可选** | **类型**        | **描述**              |
| ------------------- | -------- | --------------- | --------------------- |
| **VENDORCODE**      | 必选     | String          | 厂商代码              |
| **LOTNO**           | 必选     | String          | 批号                  |
| **PRODUCTID**       | 必选     | String          | 机种                  |
| **EQPNAME**         | 必选     | String          | 机台号                |
| **EQPTYPE**         | 必选     | String          | 机台类型              |
| **PRODUCTLINECODE** | 必选     | String          | 线别                  |
| **STEPNAME**        | 必选     | String          | 测试站站别            |
| **QUANTITY**        | 必选     | Int             | 测试数量              |
| **BINS**            | 必选     | List<BINS>      | 测试良品分BIN数量明细 |
| **STATISTICS**      | 可选     | List<STATISTIC> | 统计信息明细[         |

#### 1.2.1 BINS定义

| **名称**     | **可选** | **类型** | **描述**                              |
| ------------ | -------- | -------- | ------------------------------------- |
| **TESTERNO** | 必选     | String   | 测试箱号(只有OSD會用到，其他默認: F ) |
| **BINBOX**   | 必选     | String   | 良品项目BinBox ，若没有请写F          |
| **BIN**      | 必选     | String   | 良品项目Bin级                         |
| **QTY**      | 必选     | Int      | 良品数量                              |

#### 1.2.2 STATISTICS定义

| **名称** | **可选** | **类型** | **描述** |
| -------- | -------- | -------- | -------- |
| **NAME** | 必选     | String   | 项目名称 |
| **MIN**  | 必选     | Float    | 最小值   |
| **MAX**  | 必选     | Float    | 最大值   |
| **AVG**  | 必选     | Float    | 均值     |
| **STD**  | 必选     | Float    | 标准差   |

### 1.3.0 JSON

```json
{
    "appid": "ccd56e18846f466b8d313df6a9f857aa",
    "terminal":"你的电脑名称",
    "data": {
        "VENDORCODE": "109912",
        "LOTNO": "2013011234",
        "PRODUCTID": "LTST-19278",
        "EQPNAME": "22T101",
        "EQPTYPE": "TESTER",
        "PRODUCTLINECODE": "22",
        "STEPNAME": "2213101-2301",
        "QUANTITY":"30000",
        "BINS": [{
                "TESTERNO": "测试箱号",
                "BINBOX": "F1", 
                "BIN": "1",
                "QTY": "10000"
            },
            {
                "TESTERNO": "测试箱号",
                "BINBOX": "F2",
                "BIN": "2",
                "QTY": "120000"
            }
        ]
,
        "STATISTICS": [{
                "NAME": "VF1",
                "MIN": "3.1",
                "MAX": "3.4",
                "AVG":"3.2",
                "STD":"0.052"
            },
            {
                "NAME": "LOP1",
                "MIN": "963.7",
                "MAX": "1050.8",
                "AVG":"1020.5",
                "STD":"1.32"
            }
        ] 
    }
}

```







 





































 





  

  