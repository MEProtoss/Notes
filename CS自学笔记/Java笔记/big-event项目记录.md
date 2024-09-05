07/03/2024

## 参数校验

- spring valadation框架
- 正则表达式
- @Validated 注解 + @Pattern注解

### 参数校验失败的处理

- 全局异常处理器
- @RestControllerAdvice 由于是@restxxx 所以所有的结果都会变成json字符串响应给浏览器
- @ExceptionHandler
- 返回值类型为result
