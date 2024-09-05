# 短信登录
## 发送短信验证码

### 流程

提交手机号 -> 校验手机号 -> 生成验证码 -> 保存验证码到session -> 发送验证码

## 实现短信验证码登录和注册

- 前台发送的数据格式是json的样式 后台要用@RequestBody接收 用实体类接收
- 登录成功之后要把用户信息存储到session中 ，session的原理

## 登录校验

- 有很多controller都需要校验登录状态，所以引入spiringmvc中的拦截器

## 隐藏用户敏感信息

## 集群的session共享问题

##  Redis 代替session

- 以手机号为key 验证码为value
- 使用hash结构保存用户信息到redis key用随机token 
- 综上 俗称jwt
- 
