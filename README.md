To reproduce, install the distribution:

```
./gradlew installDist
cd build/install/demo/bin
```

Generate archive, Ctrl-C once the application has started:
```
JAVA_OPTS=-XX:ArchiveClassesAtExit=application.jsa ./demo
```

Start the application with the archive:
```
JAVA_OPTS=-XX:SharedArchiveFile=application.jsa ./demo
```

Note the failure:
```
2022-05-18 16:40:53.148 ERROR 24589 --- [           main] o.s.boot.SpringApplication               : Application run failed

org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'controllerEndpointHandlerMapping' defined in class path resource [org/springframework/boot/actuate/autoconfigure/endpoint/web/servlet/WebMvcEndpointManagementContextConfiguration.class]: Invocation of init method failed; nested exception is java.lang.NullPointerException
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1804) ~[spring-beans-5.3.19.jar:5.3.19]
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:620) ~[spring-beans-5.3.19.jar:5.3.19]
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:542) ~[spring-beans-5.3.19.jar:5.3.19]
	at org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:335) ~[spring-beans-5.3.19.jar:5.3.19]
	at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:234) ~[spring-beans-5.3.19.jar:5.3.19]
	at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:333) ~[spring-beans-5.3.19.jar:5.3.19]
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:208) ~[spring-beans-5.3.19.jar:5.3.19]
	at org.springframework.beans.factory.support.DefaultListableBeanFactory.preInstantiateSingletons(DefaultListableBeanFactory.java:953) ~[spring-beans-5.3.19.jar:5.3.19]
	at org.springframework.context.support.AbstractApplicationContext.finishBeanFactoryInitialization(AbstractApplicationContext.java:918) ~[spring-context-5.3.19.jar:5.3.19]
	at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:583) ~[spring-context-5.3.19.jar:5.3.19]
	at org.springframework.boot.web.servlet.context.ServletWebServerApplicationContext.refresh(ServletWebServerApplicationContext.java:145) ~[spring-boot-2.6.7.jar:2.6.7]
	at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:740) ~[spring-boot-2.6.7.jar:2.6.7]
	at org.springframework.boot.SpringApplication.refreshContext(SpringApplication.java:415) ~[spring-boot-2.6.7.jar:2.6.7]
	at org.springframework.boot.SpringApplication.run(SpringApplication.java:303) ~[spring-boot-2.6.7.jar:2.6.7]
	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1312) ~[spring-boot-2.6.7.jar:2.6.7]
	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1301) ~[spring-boot-2.6.7.jar:2.6.7]
	at com.example.demo.DemoApplication.main(DemoApplication.java:10) ~[demo-0.0.1-SNAPSHOT-plain.jar:na]
Caused by: java.lang.NullPointerException: null
	at java.base/java.util.LinkedHashMap$LinkedKeySet.forEach(LinkedHashMap.java:589) ~[na:na]
	at java.base/java.util.Collections$UnmodifiableCollection.forEach(Collections.java:1092) ~[na:na]
	at org.springframework.boot.actuate.endpoint.web.servlet.ControllerEndpointHandlerMapping.initHandlerMethods(ControllerEndpointHandlerMapping.java:80) ~[spring-boot-actuator-2.6.7.jar:2.6.7]
	at org.springframework.web.servlet.handler.AbstractHandlerMethodMapping.afterPropertiesSet(AbstractHandlerMethodMapping.java:213) ~[spring-webmvc-5.3.19.jar:5.3.19]
	at org.springframework.web.servlet.mvc.method.annotation.RequestMappingHandlerMapping.afterPropertiesSet(RequestMappingHandlerMapping.java:205) ~[spring-webmvc-5.3.19.jar:5.3.19]
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.invokeInitMethods(AbstractAutowireCapableBeanFactory.java:1863) ~[spring-beans-5.3.19.jar:5.3.19]
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1800) ~[spring-beans-5.3.19.jar:5.3.19]
	... 16 common frames omitted
```
