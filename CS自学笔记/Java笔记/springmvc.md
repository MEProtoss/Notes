# 荣姐SpringMVC教程

## 1.什么是SpringMVC

- 它是基于MVC开发模式的框架,用来优化控制器.它是Spring家族的一员.它也具备IOC和AOP.

- 什么是MVC?
  > 它是一种开发模式,它是模型视图控制器的简称.所有的web应用都是基于MVC开发.
  > M:模型层,包含实体类,业务逻辑层,数据访问层
  > V:视图层,html,javaScript,vue等都是视图层,用来显现数据
  > C:控制器,它是用来接收客户端的请求,并返回响应到客户端的组件,Servlet就是组件

## 7 SpringMVC的执行流程

- 核心是DispacherServelet

## 8 基于注解的SpringMVC框架的开发步骤

1. 新建项目，选择webapp模板
2. 修改目录 添加test，java，resources(两套) ，并修改目录属性3.修改pom.xml文件,添加SpringMVC的依赖,添加Servlet的依赖
   <dependency>
   <groupId>org.springframework</groupId>
   <artifactId>spring-webmvc</artifactId>
   <version>5.2.5.RELEASE</version>
   </dependency>
   <!--添加servlet的依赖-->
   <dependency>
   <groupId>javax.servlet</groupId>
   <artifactId>javax.servlet-api</artifactId>
   <version>3.1.0</version>
   </dependency>
3. 在web.xml中注册SpringMVC框架（所有的web请求都是基于servlet的)
4. 删除index.jsp,并新建，发送请求给服务器。
5. 开发控制器（Servlet），它是一个普通的类。
6. 添加tomcat进行测试功能
