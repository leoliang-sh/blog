## spring boot环境变量配置的一个问题

@Value注解通过enviroment获取对应的属性。获取的途径是：

- 获取Enviroment实例
- 获取注册的PropertySource
- 从每一个Property调用get方法获取属性

yaml文件中获取属性的规则是：

- `:`转化成`.`
- 大小写不变

环境变量中获取属性的规则是：

- `_`转化城`.`
- 不区分大小写