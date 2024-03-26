# 日程管理案例开发

## 项目搭建

### 准备数据库

- 创建数据库的连接

### 新建javaweb项目(mvc 架构模式)

- **M**：Model 模型层,具体功能如下

  1. 存放和数据库对象的实体类以及一些用于存储非数据库表完整相关的VO对象
  2. 存放一些对数据进行逻辑运算操作的的一些业务处理代码

- **V**：View 视图层,具体功能如下

  1. 存放一些视图文件相关的代码 html css js等
  2. 在前后端分离的项目中,后端已经没有视图文件,该层次已经衍化成独立的前端项目

- **C**：Controller 控制层,具体功能如下

  1. 接收客户端请求,获得请求数据
  2. 将准备好的数据响应给客户端


- dao

> dao层封装对表格数据的crud方法

> 导入JDBCUtil连接池工具类并准备jdbc.properties配置文件

> 使用接口和实现类的架构 减少不同数据库表之间的耦合

- pojo

> pojo/beans/entities 封装实体类

  > 在MVC架构中，POJO包来和数据库里的表对应，其中属性名为表中的字段名

- sevice

> 存放具体的业务方法

> service层也是根据具体的表来定义 一个表对应一组接口和实现类

- Controller


- 使用severlet技术针对不同的表格来响应用户的请求

- Controller层不需要以接口和实现类的结构架设



- util

### 导入依赖

- lombok 用于使用标签自动生成getter setter equals hashcode 构造器

- @AllArgsConstructor
- @NoArgsConstructor
- @Data

###
