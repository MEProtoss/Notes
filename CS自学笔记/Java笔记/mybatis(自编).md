## 参照mybatis中文网

<https://mybatis.net.cn/getting-started.html>

### ORM 对象 关系 映射(object relational mapping)

- 类对应表名
- 类的属性对应字段
- 类的对象对应每一条记录

## mybatis 入门程序步骤

- 配置xml 引入依赖

```xml
<dependencies>
  <!-- Mybatis核心 -->
  <dependency>
    <groupId>org.mybatis</groupId>
    <artifactId>mybatis</artifactId>
    <version>3.5.7</version>
  </dependency>
  <!-- junit测试 -->
  <dependency>
    <groupId>junit</groupId>
    <artifactId>junit</artifactId>
    <version>4.12</version>
    <scope>test</scope>
  </dependency>
  <!-- MySQL驱动 -->
  <dependency>
    <groupId>mysql</groupId>
    <artifactId>mysql-connector-java</artifactId>
    <version>5.1.3</version>
  </dependency>
</dependencies>
```

- 在resource目录下创建核心配置文件`mybatis-config`
- [ ] 用于获取数据源
```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE configuration
        PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-config.dtd">
<configuration>
    <environments default="development">
        <environment id="development">
            <transactionManager type="JDBC"/>
            <dataSource type="POOLED">
                <property name="driver" value="com.mysql.cj.jdbc.Driver"/>
                <property name="url"
                          value="jdbc:mysql://localhost:3306/mybatis"/>
                <property name="username" value="root"
                <property name="password" value="990418"/>
            </dataSource>
        </environment>
    </environments>

    <!--    加载sql映射的配置文件 -->
    <mappers>
        <mapper resource="UserMapper.xml"/>
    </mappers>
</configuration>
```

- 在resource目录下创建sql映射文件
- [ ] 命名为${表名}Mapper.xml 用于编写操作对应表的sql语句 
```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper
        PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
<!--命名空间-->
<mapper namespace="nm">
    <select id="selectAll" resultType="com.chenhao.pojo.User">
        select * from tb_user
    </select>
</mapper>
```
- 注意！sql查询语句中间不能有注释！！！

- 编写pojo实体类 对应数据库表的orm 表里的字段全都定义成属性 然后生成set get方法。
```java

package com.chenhao.pojo;

/**
 * ClassName: User
 * Package: com.chenhao.pojo
 * Description:
 *
 * @Author CHEN
 * @Create 2023/12/12 上午11:05
 * @Version 1.0
 */
public class User {
   private Integer id;
   private String username;
   private String password;
   private String gender;
   private String addr;

    public Integer getId() {
        return id;
    }

    public void setId(Integer id) {
        this.id = id;
    }

    public String getUsername() {
        return username;
    }

    public void setUsername(String username) {
        this.username = username;
    }

    public String getPassword() {
        return password;
    }

    public void setPassword(String password) {
        this.password = password;
    }

    public String getGender() {
        return gender;
    }

    public void setGender(String gender) {
        this.gender = gender;
    }

    public String getAddr() {
        return addr;
    }

    public void setAddr(String addr) {
        this.addr = addr;
    }

    @Override
    public String toString() {
        return "User{" +
                "id=" + id +
                ", username='" + username + '\'' +
                ", password='" + password + '\'' +
                ", gender='" + gender + '\'' +
                ", addr='" + addr + '\'' +
                '}';
    }
}
```


- 编写测试类

```java

package com.chenhao;

import com.chenhao.pojo.User;
import org.apache.ibatis.io.Resources;
import org.apache.ibatis.session.SqlSession;
import org.apache.ibatis.session.SqlSessionFactory;
import org.apache.ibatis.session.SqlSessionFactoryBuilder;

import java.io.IOException;
import java.io.InputStream;
import java.util.List;

/**
 * ClassName: mybatisDemo
 * Package: com.chenhao.com.chen.test
 * Description:
 *
 * @Author CHEN
 * @Create 2023/12/12 上午11:12
 * @Version 1.0
 */
public class mybatisDemo {
    public static void main(String[] args) throws IOException {
      //这三行是通过工厂创建sqlSession
        String resource = "mybatis-config.xml";
        InputStream inputStream = Resources.getResourceAsStream(resource);
        SqlSessionFactory sqlSessionFactory = new SqlSessionFactoryBuilder().build(inputStream);

// 开启sqlSession
        SqlSession sqlSession = sqlSessionFactory.openSession();

        List<User> users = sqlSession.selectList("nm.selectAll");

        System.out.println(users);
//释放资源
        sqlSession.close();

    }
}
```

## idea与数据库建立连接

## mybatis核心配置
* configuration（配置）
* properties（属性）
* settings（设置）
* typeAliases（类型别名）
* typeHandlers（类型处理器）
* objectFactory（对象工厂）
* plugins（插件）
* environments（环境配置）
* environment（环境变量）
* transactionManager（事务管理器）
* dataSource（数据源）
* databaseIdProvider（数据库厂商标识）
* mappers（映射器）

## 数据库表的字段名称和实体类的属性名称不一样，则不能自动封装数据

- [ ] 使用resultMap标签
```xml
<!-- 
1.定义<resultMap>标签
2.在<select>标签中，使用resultMap属性代替resultType属性
    id 是唯一标识
    type 映射的类型 支持别名

-->
<resultMap id="brandResultMap" type="brand">
    <result column="brand_name" property="brandName"/>
    <result column="company_name" property="companyName"/>
</resultMap>

```

## 多条件查询

- sql语句设置多个参数的三种方式
- 使用 `@Param("参数名称")` 标记每一个参数，在映射配置文件中就需要使用 `#{参数名称}` 进行占位
  
  ```java
  List<Brand> selectByCondition(@Param("status") int status, @Param("companyName") String companyName,@Param("brandName") String brandName);
  ```
  
- 将多个参数封装成一个 实体对象 ，将该实体对象作为接口的方法参数。该方式要求在映射配置文件的SQL中使用 `#{内容}` 时，里面的内容必须和实体类属性名保持一致。
  
  ```java
  List<Brand> selectByCondition(Brand brand);
  ```
  
- 将多个参数封装到map集合中，将map集合作为接口的方法参数。该方式要求在映射配置文件的SQL中使用 `#{内容}` 时，里面的内容必须和map集合中键的名称一致。
  
  ```
  List<Brand> selectByCondition(Map map);
  ```


## 动态条件查询
- if标签
```xml
    <!--动态条件查询
        if标签里要用对应值的字符串 而不是字段名称
        if :条件判断
         * test：逻辑表达式
        * 问题：第一个条件不需要逻辑运算符
            * 恒等式 1=1
            * <where>标签 替换 where 关键字（推荐
    -->
 <select id="selectByCondition" resultMap="brandResultMap">brandsbrandsbrandsbrandsbrandsbrandsbrandsbrandsbrandsbrandsbrandsbrandsbrands
        select *
        from tb_brand
        /*where 1=1*/
        <where>

            <if test="status != null">

                and status = #{status}
            </if>
            <if test="companyName != null and companyName != '' ">

                and company_name like #{companyName}
            </if>

            <if test="brandName != null and brandName != '' ">

                and brand_name like #{brandName};
            </if>
        </where>
    </select>
</mapper>
```

## 添加

- 主键返回
```xml
 <insert useGeneratedKeys="true" keyProperty="id">
```

## 修改

- 修改全部字段
```xml

    <update id="update">
        update tb_brand
        set brand_name   = #{brandName},
            company_name = #{companyName},
            ordered      = #{ordered},
            description  = #{description},
            status       = #{status}
        where id = #{id};
    </update>
```

- 修改动态字段
- [ ] 使用<set>标签代替set关键字 然后用<if>标签来做条件判断
```xml
    <update id="update">
        update tb_brand
        <set>

            <if test="brandName != null and brandName != '' ">
                brand_name = #{brandName},
            </if>
            <if test="companyName != null and companyName != '' ">
                company_name = #{companyName},
            </if>
            <if test="ordered != null">
                ordered = #{ordered},
            </if>
            <if test="description != null and description != '' ">
                description = #{description},
            </if>
            <if test="status != null and status != '' ">
                status = #{status}
            </if>
        </set>

        where id = #{id};


    </update>
```

## 删除
### 删除一个
```xml

    <delete id="deleteById">
        delete
        from tb_brand
        where id = #{id};
    </delete>
```

### 批量删除
```xml
<!--    批量删除
mybatis会将 数组的参数 封装为一个map集合
* 默认array=数组 （键值对）
* 可使用@Para注解改变map集合的默认key的名称 (collection标签)
-->
    <delete id="deleteByIds">
        delete
        from tb_brand
        where id in
            <foreach collection="ids" item="id" separator="," open="(" close=")">
                #{id}
            </foreach>
            ;
    </delete>
</mapper>```

## mybatis参数传递

Mybatis 接口方法中可以接收各种各样的参数，如下：

- 多个参数
- 单个参数：单个参数又可以是如下类型
  - POJO 类型
  - Map 集合类型
  - Collection 集合类型
  - List 集合类型
  - Array 类型
  - 其他类型

  结论：以后接口参数是多个时，在每个参数上都使用 `@Param`
  注解。这样代码的可读性更高。

## 注解开发
* 注解是用来替换映射配置文件方式配置的，所以使用了注解，就不需要再映射配置文件中书写对应的 `statement`

* 解完成简单功能，配置文件完成复杂功能。

- [ ] 格式
```java
    @Select("select * from tb_user where id = #{id};")
    User selectById(int id);
```

* 加上对应注解 ，然后注解里编写sql语句即可。

