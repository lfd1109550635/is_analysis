
# 实验5：图书管理系统数据库设计与界面设计
|学号|班级|姓名|照片|
|:-------:|:-------------: | :----------:|:---:|
|201610414412|软件(本)16-4|林福岽|![flow1](../myself.jpg)|

## 1.数据库表设计

## 1.1. 图书表
|字段|类型|主键，外键|可以为空|默认值|约束|说明|
|:-------:|:-------------:|:------:|:----:|:---:|:----:|:-----|
|ISBN|varchar2(100)|主键|否|||编号|
|BookName|varchar2(100)| |否|||图书名称|
|class|varchar2(100)| |是|||图书类别|
|auhur|varchar2(100)| |是|||作者|
## 1.2. 读者表
|字段|类型|主键，外键|可以为空|默认值|约束|说明|
|:-------:|:-------------:|:------:|:----:|:---:|:----:|:-----|
|ISBN|varchar2(100)|主键|否|||学号|
|BookName|varchar2(100)| |否|||姓名|
|Sex|varchar2(100)| |是|||性别|
|grade|varchar2(100)| |是|||年级|
|major|varchar2(100)| |是|||专业|
## 1.3. 图书借阅信息表
|字段|类型|主键，外键|可以为空|默认值|约束|说明|
|:-------:|:-------------:|:------:|:----:|:---:|:----:|:-----|
|ISBN|varchar2(100)|主键|否|||借出图书编号|
|BookName|varchar2(100)| |否|||书名|
|out date|varchar2(100)| |是|||借书日期|
|back date|varchar2(100)| |是|||还书日期|
|compensation|varchar2(100)| |是|||赔偿金额|
## 1.4. 图书管理员表
|字段|类型|主键，外键|可以为空|默认值|约束|说明|
|:-------:|:-------------:|:------:|:----:|:---:|:----:|:-----|
|ISBN|varchar2(100)|主键|否|||管理员ID|
|Name|varchar2(100)| |否|||姓名|
|lavel|varchar2(100)| |是|||权限|
|password|varchar2(100)| |是|||密码|
## 2. 界面设计
## 2.1. 主界面设计
![pic1](https://github.com/lfd1109550635/is_analysis/blob/master/test5/借书界面.png)
- 用例图参见：借书用例
- 类图参见：借书类，读者类
- 顺序图参见：借书顺序图
- API接口如下：

1. 读者信息API

- 功能：读者信息（直接从数据库中获取）
- 请求地址：C:\Users\18283851939\Desktop\新建文件夹\index.html
- 请求方法：POST
- 请求参数：

|参数名称|必填|说明|
|:-------:|:-------------: | :----------:|
|id|是|用户uid |
|access_token|是|用于验证请求合法性的认证信息。 |
|method|是|固定为 “GET”。|

- 返回实例：
```
{

    "info": "返回成功",

    "data": {

        "uid": "14361",

        "nickname": 林福岽",

        "sex": "0",

        "birthday": "0000-00-00",

        "qq": "",

        "login": "127",

        "reg_ip": "1862470573",

        "reg_time": "1489058706",

        "last_login_ip": "1862470573",

        "last_login_time": "1499667768",

        "status": "1",

        "last_login_role": "1",

        "show_role": "1",

        "signature": "啊",

        "pos_province": "330000",

        "pos_city": "330400",

        "pos_district": "330483",

        "pos_community": "0",

        "score1": "322",

        "score2": "0",

        "score3": "0",

        "score4": "0",

        "con_check": "0",

        "total_check": "2",

        "score6": "0",

        "score8": "69",

        "fans": "3",

        "session_id": "asilmq7fskbootlufsnu9qhlb4"

    },

    "code": 200

}
```
- 返回参数说明：
    
|参数名称|说明|
|:-------:|:-------------: |
|Info|返回信息|
|data|用户的个人信息|
|dodo|返回码|

2. 管理员信息API
- 功能：管理员信息（直接从数据库中获取）
- 请求地址：C:\Users\18283851939\Desktop\新建文件夹\page1.html
- 请求方法：POST
- 请求参数：

|参数名称|必填|说明|
|:-------:|:-------------: | :----------:|
|id|是|管理员uid |
|password|是|管理员upassword |
|access_token|是|用于验证请求合法性的认证信息。 |
|method|是|固定为 “GET”。|

- 返回实例：
```
{

    "info": "返回成功",

    "data": {

        "uid": "14361",

        "nickname": "wmr",

        "sex": "0",

        "birthday": "0000-00-00",

        "qq": "",

        "login": "127",

        "reg_ip": "1862470573",

        "reg_time": "1489058706",

        "last_login_ip": "1862470573",

        "last_login_time": "1499667768",

        "status": "1",

        "last_login_role": "1",

        "show_role": "1",

        "signature": "啊",

        "pos_province": "330000",

        "pos_city": "330400",

        "pos_district": "330483",

        "pos_community": "0",

        "score1": "322",

        "score2": "0",

        "score3": "0",

        "score4": "0",

        "con_check": "0",

        "total_check": "2",

        "score6": "0",

        "score8": "69",

        "fans": "3",

        "session_id": "asilmq7fskbootlufsnu9qhlb4"

    },

    "code": 200

}
```
- 返回参数说明：
    
|参数名称|说明|
|:-------:|:-------------: |
|Info|返回信息|
|data|的个人信管理员息|
|dodo|返回码|
3. 图书信息API
- 功能：图书信息（直接从数据库中获取）
- 请求地址：C:\Users\18283851939\Desktop\新建文件夹\page2.html
- 请求方法：POST
- 请求参数：

|参数名称|必填|说明|
|:-------:|:-------------: | :----------:|
|id|是|图书编号 |
|access_token|是|用于验证请求合法性的认证信息。 |
|method|是|固定为 “GET”。|

- 返回实例：
```
{

    "info": "返回成功",

    "data": {

        "uid": "14361",

        "nickname": "wmr",

        "sex": "0",

        "birthday": "0000-00-00",

        "qq": "",

        "login": "127",

        "reg_ip": "1862470573",

        "reg_time": "1489058706",

        "last_login_ip": "1862470573",

        "last_login_time": "1499667768",

        "status": "1",

        "last_login_role": "1",

        "show_role": "1",

        "signature": "啊",

        "pos_province": "330000",

        "pos_city": "330400",

        "pos_district": "330483",

        "pos_community": "0",

        "score1": "322",

        "score2": "0",

        "score3": "0",

        "score4": "0",

        "con_check": "0",

        "total_check": "2",

        "score6": "0",

        "score8": "69",

        "fans": "3",

        "session_id": "asilmq7fskbootlufsnu9qhlb4"

    },

    "code": 200

}
```
- 返回参数说明：
    
|参数名称|说明|
|:-------:|:-------------: |
|Info|返回信息|
|data|的图书信管理员息|
|dodo|返回码|
