# Spring的生命周期

​	何为Spring的生命周期，简单的理解就是，从程序运行开始到程序结束Spring所做的有哪些操作。

## 一、注解方式的生命周期

​	首先看一下的代码

```java
public static void main(String[] args) {
	// 通过这个类可以加载标记了@Component（或@Component子类）
  AnnotaionConfigApplicationContext context = new AnnotationConfigApplicationContext();
  context.register(AppConfig.class);
  context.refresh();
  
  UserDaoImpl userDao = (UserDaoImpl) context.getBean("userDaoImpl");
  userDao.query();
}
```

````java
@Configuration
@Component("com.yinxy")
public class AppConfig {	
}
````

​	因为是注解方式的生命周期，所以我们会通过AnnotaionConfigApplicationContext来加载类。如果通过reigister()来加载类的话，需要手动的进行refresh()。