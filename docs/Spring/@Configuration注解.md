@Configuration注解的proxyBeanMethods属性：

​	直译为代理bean方法，默认为true，表示配置的bean为一个该类型的代理对象，而不是该类型对象

​	显示申明为false则配置的bean即为该类型的对象



> 代理对象和真实对象的区别：能够解决循环依赖问题