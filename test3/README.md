# 实验3：图书管理系统领域对象建模（老师示范）
|学号|班级|姓名|照片|
|:-------:|:-------------: | :----------:|:---:|
|201610414412|软件(本)16-4|林福岽|![flow1](../myself.jpg)|

## 1. 图书管理系统的类图

### 1.1 类图PlantUML源码如下：

``` class
@startuml
class 新图书{
作者
出版社
出版日期
(入库)
}
class 经销商{
名称
(提供新图书)
}
class 订单 {
书名
数量
价格
(传递)
}
class 分编员 {
职工号
姓名
(图书分类编号)
}
class 采购员 {
职工号
姓名
(购买图书)
}
class 罚款细则{
未定
}
class 逾期记录{
逾期天数
(增)
(删)
(查)
(改)
}
class 图书管理员{
职工号
姓名
(预定管理）
(借书管理）
(还书管理）
(保存图书）
(给采购员授权下单)
(维护读者信息)
}
class 借书记录 {
借书日期
归还日期
(增)
(删)
(查)
(改)
}
class 资源项 {
馆藏流水号
状态
(增)
(删)
(查)
(改)
}
class 图书品种 {
作者
出版社
出版日期
(增)
(删)
(查)
(改)
}
class 馆藏目录{
书信息
(增)
(删)
(查)
(改)
}
class 图书馆书类品 {
图书名称
图书编号
简介
馆藏数量
可借数量
(增)
(删)
(查)
(改)
}
class 预定记录 {
预定日期
}
class 读者{
姓名
身份证号码
卡号
(查阅管理)
(信息管理)
(预定图书)
(取消图书)
}
读者 "0..*"--|> 预定记录
预定记录"0..*" --|> 图书馆书类品 : 被预定或被取消预订
图书馆书类品"0..*" -* 资源项  : 拥有
图书馆书类品"0..*" -* 馆藏目录  : 拥有
图书馆书类品"0..*" -* 图书品种  : 拥有
借书记录"0..*" --|> 读者
图书管理员"0..*" --|> 借书记录 : 登记
逾期记录"0..*" -- 借书记录
罚款细则<|-- "1"逾期记录 : 使用
图书管理员"0..*" --|> 图书馆书类品 : 维护书目
图书管理员"0..*" --|> 读者 : 维护读者信息
读者"1" --|> 图书馆书类品 : 查询书目
图书管理员"1" --|> 采购员
采购员"1" --|> 订单
经销商"0..*" --|> 新图书
订单"1" --|>  经销商
新图书 <|-- "0..*"分编员
新图书"1" --|> 图书馆书类品
@enduml
```

### 1.2. 类图如下：

参见图8.17

![class](https://github.com/lfd1109550635/is_analysis/blob/master/test3/实验三类图1.png)

### 1.3. 类图说明：
说明文字***

## 2. 图书管理系统的对象图
### 2.1 类***的对象图
#### 源码如下：
``` class
@startuml
object 图书管理员

图书管理员 : 职工号：1231561321653123
图书管理员 : 姓名 = 撒旦金克拉就

@enduml
``` 
#### 对象图如下：
![class](https://github.com/lfd1109550635/is_analysis/blob/master/test3/对象图1.png)

### 2.2 类***的对象图
#### 源码如下：
``` class
@startuml
object 读者

读者 : 身份证卡号 = 1231564321
读者 : 姓名 = 啊实打实的
读者 : 卡号 = 123156132
@enduml
``` 
#### 对象图如下：
![class](https://github.com/lfd1109550635/is_analysis/blob/master/test3/对象图2.png)

类***的对象图
#### 源码如下：
``` class
@startuml
object 罚款细则
罚款细则 :  罚款2000元
@enduml
``` 
#### 对象图如下：
![class](https://github.com/lfd1109550635/is_analysis/blob/master/test3/对象图3.png)

类***的对象图
#### 源码如下：
``` class
@startuml
object 逾期记录
逾期记录 : 书名=好难受
逾期记录 : 编号=5641321
逾期记录 : 时间=28小时
@enduml
``` 
#### 对象图如下：
![class](https://github.com/lfd1109550635/is_analysis/blob/master/test3/对象图4.png)


类***的对象图
#### 源码如下：
``` class
@startuml
object 借书记录
借书记录 : 书名=好麻烦
借书记录 : 编号=52
借书记录 : 时间=24小时

@enduml
``` 
#### 对象图如下：
![class](https://github.com/lfd1109550635/is_analysis/blob/master/test3/对象图5.png)


类***的对象图
#### 源码如下：
``` class
@startuml
object 采购员

采购员 : 职工号 = 1231561321653123
采购员 : 姓名 = 撒旦金克拉就
@enduml
``` 
#### 对象图如下：
![class](https://github.com/lfd1109550635/is_analysis/blob/master/test3/对象图6.png)


类***的对象图
#### 源码如下：
``` class
@startuml
object 订单

订单 : 书名=无语了
订单 : 数量 = 20
订单 : 价格 = 300
@enduml
``` 
#### 对象图如下：
![class](https://github.com/lfd1109550635/is_analysis/blob/master/test3/对象图7.png)


类***的对象图
#### 源码如下：
``` class
@startuml
object 经销商

经销商 : 名称=我擦勒
@enduml
``` 
#### 对象图如下：
![class](https://github.com/lfd1109550635/is_analysis/blob/master/test3/对象图8.png)


类***的对象图
#### 源码如下：
``` class
@startuml
object 新图书

新图书 : 作者=嘿嘿
新图书 : 出版社=社会社会社
新图书 : 出版日期=9.12
@enduml
``` 
#### 对象图如下：
![class](https://github.com/lfd1109550635/is_analysis/blob/master/test3/对象图9.png)


类***的对象图
#### 源码如下：
``` class
@startuml
object 预定记录

预定记录 : 预定日期=1.2

@enduml
``` 
#### 对象图如下：
![class](https://github.com/lfd1109550635/is_analysis/blob/master/test3/对象图10.png)


类***的对象图
#### 源码如下：
``` class
@startuml
object 图书馆书类品

图书馆书类品 : 图书名称=撒旦很健康
图书馆书类品 : 图书编号=425
图书馆书类品 : 简介=好看得很
图书馆书类品 : 馆藏数量=43
图书馆书类品 : 可借数量=12

@enduml
``` 
#### 对象图如下：
![class](https://github.com/lfd1109550635/is_analysis/blob/master/test3/对象图11.png)


类***的对象图
#### 源码如下：
``` class
@startuml
object 馆藏目录

馆藏目录 : 书信息=撒旦很健康

@enduml
``` 
#### 对象图如下：
![class](https://github.com/lfd1109550635/is_analysis/blob/master/test3/对象图12.png)


类***的对象图
#### 源码如下：
``` class
@startuml
object 资源项

资源项 : 馆藏流水号=48545
资源项 : 状态=已借出
@enduml
``` 
#### 对象图如下：
![class](https://github.com/lfd1109550635/is_analysis/blob/master/test3/对象图13.png)


类***的对象图
#### 源码如下：
``` class
@startuml
object 图书品种

图书品种 : 作者=撒旦
图书品种 : 出版社=发达的
图书品种 : 出版日期=8.14

@enduml
``` 
#### 对象图如下：
![class](https://github.com/lfd1109550635/is_analysis/blob/master/test3/对象图14.png)


类***的对象图
#### 源码如下：
``` class
@startuml
object 分编员

分编员 : 职工号=54694545667
分编员 : 姓名= 撒大窟窿

@enduml
``` 
#### 对象图如下：
![class](https://github.com/lfd1109550635/is_analysis/blob/master/test3/对象图15.png)


