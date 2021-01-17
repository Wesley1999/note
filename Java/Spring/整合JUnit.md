# 整合JUnit

## maven依赖
```
	<!-- junit -->
	<dependency>
    	<groupId>junit</groupId>
    	<artifactId>junit</artifactId>
    	<version>4.12</version>
    	<scope>test</scope>
	</dependency>
	<!-- spring-test -->
	<dependency>
	    <groupId>org.springframework</groupId>
	    <artifactId>spring-test</artifactId>
	    <version>4.3.9.RELEASE</version>
	    <scope>test</scope>
	</dependency>
```

## 类名添加注解
```java
@RunWith(SpringJUnit4ClassRunner.class)
@ContextConfiguration(locations = { "classpath*:/application-context-test.xml"})
```

## 完整示例
```
import cn.com.topsec.display.mapper.AppMapper;
import cn.com.topsec.display.pojo.*;
import org.junit.Test;
import org.junit.runner.RunWith;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.test.context.ContextConfiguration;
import org.springframework.test.context.junit4.SpringJUnit4ClassRunner;

import java.util.List;

@RunWith(SpringJUnit4ClassRunner.class)
@ContextConfiguration(locations = {"classpath*:/applicationContext.xml"})
public class MyTest {

    @Autowired
    AppMapper appMapper;

    @Test
    public void insertToCveApp() {
        AppExample appExample = new AppExample();
        appExample.createCriteria().andIdNotEqualTo(Integer.MAX_VALUE);
        List<App> apps = appMapper.selectByExample(appExample);
        for (App app : apps) {
            System.out.println(app);
        }
    }

}
```

## Reference
https://blog.csdn.net/fuck487/article/details/78562312