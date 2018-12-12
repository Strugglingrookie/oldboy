#选课系统
***
###程序说明：
    管理基础信息 + 选课系统

###实现功能如下：
    选课系统开发，要求有四种角色:学校、学员、课程、讲师
    详细要求:
    创建北京、上海 2 所学校
    创建linux , python , go 3个课程 ， linux\py 在北京开， go 在上海开
    课程包含，周期，价格，通过学校创建课程
    通过学校创建班级， 班级关联课程、讲师
    创建学员时，选择学校，关联班级
    创建讲师角色时要关联学校
    提供两个角色接口
    为学员、讲师、管理员分别提供用户界面，并提供对应功能：
    1 学员视图， 可以注册， 交学费， 选择班级，
    2 讲师视图， 讲师可管理自己的班级， 上课时选择班级， 查看班级学员列表 ， 修改所管理的学员的成绩
    3 管理视图，创建讲师， 创建班级，创建课程
    注1：上面的操作产生的数据都通过pickle序列化保存到文件里   注2：此作业必须画流程图，图中标注好不同类或对象之间的调用关系

###数据分析
# 学校    数据属性： 学校名称；                                         函数属性：无
# 课程    数据属性： 学校名称 课程名 周期 价格 ；                       函数属性：无
# 教师    数据属性： 学校名称 姓名 班级列表 角色编号1；                 函数属性：选择所属班级 查看班级学生 修改班级学生成绩
# 班级    数据属性： 学校名称 班级名称 课程名 教师列表 学员列表；       函数属性：关联课程 关联讲师
# 学员    数据属性： 学校名称 班级列表 姓名 成绩 学费状态 角色编号2；   函数属性：交学费  选择班级  查看成绩
# 管理员  数据属性： 姓名 角色编号0；                                   函数属性：创建讲师 创建班级 创建课程

###程序运行：
    python course_system/manage.py

###程序结构：
   course_system/
   ├── README.md #项目说明
   ├── manage.py #启动目录，程序入口。
   │── bin # 执行文件 目录
   │   ├── start.py  #首先让用户选择登陆还是注册，注册走学生注册逻辑，注册完成后走学生视角；登陆则根据角色，走学生还教师，教师又有分支管理员还是教学
   │── config #配置文件
   │   ├── settings.py #存放学校、学员、课程、讲师、班级的目录信息
   │── src #主要程序逻辑都 在这个目录里
   │   └── course.py #管理员可以进行课程增删查
   │   └── group.py #管理员可以进行班级增删查
   │   └── login.py #登陆逻辑
   │   └── school.py #管理员可以进行学校增删查
   │   └── student.py #管理员可以进行学生增删查  学生可以注册， 交学费， 选择班级
   │   └── teacher.py #管理员可以进行教师增删查  教师可以选择班级， 查看班级学员列表 ， 修改所管理的学员的成绩
   │   └── tools.py #提供了序列化的方法，供所有模块调用
   │── db #以下数据均以json文件存储
   │   └── myclasses.pkl #班级信息
   │   └── mycourses.pkl #课程信息
   │   └── myschools.pkl #学校信息
   │   └── mystudents.pkl #学生信息
   │   └── myteachers.pkl #教师信息
   │── 数据结构.png #数据结构
   │── 流程图.png #流程图