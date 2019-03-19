# 实验1：业务流程建模（老师示范）
|学号|班级|姓名|照片|
|:-------:|:-------------: | :----------:|:---:|
|201610414412|软件(本)16-4|1.林福岽|![flow1](../myself.jpg)|

## 流程图1：考试及成绩管理流程

**PlantUML源码如下：**
'''
@startuml<br>
|教务处|<br>
-安排考试<br>
-考试安排表<br>
|教师|<br>
-出卷<br>
fork<br>
:A、B试卷;<br>
fork again<br>
:打印审批表;<br>
|系主任|<br>
-审批签字<br>
-打印审批表：<br>
end fork<br>
|教务处|<br>
-打印试卷<br>
-试卷<br>
|学生|<br>
-参加考试<br>
-答卷<br>
|教师|<br>
-阅出成绩<br>
fork<br>
:成绩单;<br>
|教务处|<br>
 -[#blue]-><br>
-有不及格？<br>
-> 有;<br>
-安排补考<br>
fork<br>
-补考安排表<br>
fork end<br>
fork again<br>
|教师|<br>
-答卷<br>
-装订存档<br>
fork end<br>
-期末流程结束<br>
@enduml
'''
**业务流程图如下：**

![flow1](flow1.jpg)

**流程说明：**

某高校对期末考试流程规定如下：期末考试前三周，教务处负责安排全校课程的考试时间和地点，<br>
下发“考试安排表”。<br>
考试前一周，各任课老师准备好A、B两份试卷，填写“试卷打印审批表”<br>
一并交与系主任审批签字，<br>
将选中的期末试卷和已签字的“试卷打印审批表”送交教务处印刷部门进行印刷。<br>
学生按时到达指定考场考试，<br>
考试完毕任课教师进行阅卷，<br>
产生成绩单，并对学生答卷装订存档。<br>
如果课程有不及格情况，教务处负责安排补考时间和地点，<br>
产生“补考安排表”<br>

## 流程图2： 客户维修服务流程

**PlantUML源码如下：**

``` flow2
@startuml
start
if (Graphviz installed?) then (yes)
:process all\ndiagrams;
else (no)
:process only
__sequence__ and __activity__ diagrams;
endif
stop
@enduml
```

**业务流程图如下：**

![flow2](flow2.jpg)

**流程说明：**

说明文字....
