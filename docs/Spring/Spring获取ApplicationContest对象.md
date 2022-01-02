### 一、Bean对象中获取

#### 1、非静态变量

可直接从容器中获取

```JAVA
/**
 * 三种注入方式：字段注入、set方法注入、构造器注入
 */
@Component
public class Demo {
    
    /**
     * 1、字段注入
     */
    @Autowired
    private ApplicationContext applicationContext;
    
    /**
     * 2、set方法注入
     */
    @Autowired
    public static void setApplicationContext(ApplicationContext context) {
        ApplicationContextUtil.applicationContext = context;
    }

    /**
 	 * 3、构造器方式注入
 	 *      如果类只提供了一个带参数的构造方法，则不需要对对其内部的属性写 @Autowired 注解，Spring 会自动为你注入属性。
 	 */
    public Demo(ApplicationContext context) {
        applicationContext = context;
    }
}	
```

#### 2、静态变量

##### 第一种：构造器注入

- 字段注入、set方法注入，这两种方式都**不能注入静态变量**

```java
/**
 * 第一种：普通方式的构造器注入
 *  
 * 字段注入、set方法注入，这两种方式都不能注入静态变量
 */
@Component
public class Demo {
    private final ApplicationContext applicationContext;

    public Demo(ApplicationContext applicationContext) {
        this.applicationContext = applicationContext;
    }
}	
```

##### 第二种：实现ApplicationContextAware接口注入

```JAVA
@Component
public class Demo implements ApplicationContextAware {
    private static ApplicationContext applicationContext;

    @Override
    public void setApplicationContext(ApplicationContext context) throws BeansException {
        applicationContext = context;
    }

    public static ApplicationContext getApplicationContext() { return applicationContext;  }
}
```

### 二、非Bean对象获取