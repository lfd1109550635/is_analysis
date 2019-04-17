# 实验4：图书管理系统顺序图绘制（老师示范）
|学号|班级|姓名|照片|
|:-------:|:-------------: | :----------:|:---:|
|201610414412|软件(本)16-4|林福岽|![flow1](../myself.jpg)|

## 图书管理系统的顺序图

## 1. 借书用例
## 1.1. 借书用例PlantUML源码

``` sequence
@startuml
skinparam sequenceArrowThickness 2
skinparam roundcorner 2
skinparam maxmessagesize 1
skinparam sequenceParticipant underline

actor 图书管理员
activate 图书管理员
participant "： 读者" as A
participant "： 资源项" as B
participant "： 馆藏书类品" as C
participant "： 借书记录" as D
A -> 图书管理员: 提供借阅卡并申请借书
activate A
deactivate A
图书管理员 -> A: 验证读者信息并判断
activate A
deactivate A
loop
图书管理员 -> B: 获取资源项
activate B
B -> C: 查找资源品种
activate C
deactivate C
deactivate B
图书管理员 -> D: 创建借书记录
activate D
deactivate D
图书管理员 -> B: 借出图书
activate B
B -> C: 减少可借数量
activate C
deactivate C
deactivate B
图书管理员 -> A: 减少可用限额
activate A
deactivate A
end
deactivate 图书管理员
@enduml
```

## 1.2. 借书用例顺序图
![class](https://github.com/lfd1109550635/is_analysis/blob/master/test4/实验四.png)

## 1.3. 借书用例顺序图说明
ABCDE....

***

## 2. 还书用例
## 2.1. 还书用例PlantUML源码

``` sequence
@startuml
skinparam sequenceArrowThickness 2
skinparam roundcorner 2
skinparam maxmessagesize 1
skinparam sequenceParticipant underline

actor 图书管理员
participant "： 资源项" as A
participant "： 借书记录" as B
participant "： 馆藏书类品" as C
participant "： 读者" as D
participant "： 逾期记录" as E
图书管理员 -> A: 读取资源信息
activate 图书管理员
activate A
A -> B: 取借书记录
activate B
deactivate B
A -> C: 取资源的品种
activate C
deactivate C
deactivate A
图书管理员 -> D: 取借阅者信息
activate D
deactivate D
图书管理员 -> A: 归还资源
activate A
A -> C: 增加可借数量
activate C
deactivate C
deactivate A
图书管理员 -> B: 登记还书日期
activate B
deactivate B
opt 逾期
图书管理员 -> E: 登记逾期记录
activate E
deactivate E
deactivate 图书管理员
end
@enduml
```

## 2.2. 还书用例顺序图
![class](https://github.com/lfd1109550635/is_analysis/blob/master/test4/实验四归还图书.png)

## 2.3. 还书用例顺序图说明
ABCDE...
***

## 3. 购书用例
## 3.1. 购书用例PlantUML源码

``` sequence
@startuml
skinparam sequenceArrowThickness 2
skinparam roundcorner 2
skinparam maxmessagesize 1
skinparam sequenceParticipant underline

actor 图书管理员
activate 图书管理员
participant "： 采购员" as A
participant "： 经销商" as B
participant "： 订单" as C

图书管理员 -> A: 发布所需购书信息
activate A
deactivate A
图书管理员 -> A: 授权
loop
activate A
A -> C : 图书信息
deactivate A
activate C
B <- C : 统计
deactivate C
activate B
A <- B : 报价
deactivate B
activate A
图书管理员 <- A : 反馈信息并申请
deactivate A
图书管理员 -> A: 批准

activate A
A -> B: 下单购买
deactivate A
activate B
图书管理员 <- B: 供货送货
deactivate B
图书管理员 -> B: 付款
activate B
deactivate B
deactivate 图书管理员
end
@enduml
```

## 3.2. 购书用例顺序图
![class](https://github.com/lfd1109550635/is_analysis/blob/master/test4/实验四购书.png)

## 3.3. 购书用例顺序图说明
ABCDE....

***
