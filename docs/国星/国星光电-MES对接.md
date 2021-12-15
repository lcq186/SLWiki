# 国星光电- MES对接

~~~mermaid
graph TB
start(启动测试仪软件)-->edit[机器编号]-->file[编辑保存记录]
start-->selectMode[选择模式]
selectMode-->loadfileMachine[机器固定资产号记录]-->loadfile{读取是否成功}
loadfile--No-->selectMode
loadfile--yes-->webAPI[Http Post 固定资产号 ]
webAPI-->Results{工单号}-->PosTester{点检测试}
Results--获取失败-->Admin{管理员密码}
Admin--写入工单号-->Results
PosTester-->check[校正测试]
check-->http[上传校验数据]
~~~

 



