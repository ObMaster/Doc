1、@JsonIgnore

序列化和反序列化时忽略该属性

2、@JsonProperty

- value	指定该属性序列化后的属性名称
- access：指定属性的访问方式
  - Access.AUTO
  - Access.READ_ONLY：该属性可以正常序列化，但是反序列化时不能被写入对象（反序列化时忽略该属性）
  - Access.WRITE_ONLY：序列化时忽略该属性，反序列化时正常写入
  - Access.READ_WRITE：既可以序列化又可以反序列化
- 

