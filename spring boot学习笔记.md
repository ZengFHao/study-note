尚硅谷学习资料

- [文档地址](http://www.yuque.com/atguigu/springboot)

- [视频地址](http://www.gulixueyuan.com)

- [源码地址](http://gitee.com/leifengyang/springboot2)

# SpringBoot学习笔记



## SpringBoot入门知识

### Spring生态圈

- 覆盖了：
  - web开发
  - 数据访问
  - 安全控制
  - 分布式
  - 消息服务
  - 移动开发
  - 批处理

### SpringBoot的提出

- **原因**：虽然Spring生态圈可以完成当前市面所有开发任务，但Spring需要整合众多的配置，SpringBoot不用关心之前Spring的各种配置，能够快速创建生产级别的Spring应用
- SpringBoot是一个高级框架：
  - 底层实现是Spring
  - Spring的底层实现是Java

- **优点**：
  - 创建独立的Spring应用
  - 内嵌web服务器
  - 提供自动的Starter依赖，简化了构建配置
    - 不需要之前一大堆Spring的jar包
    - 如果要进行web开发，只需要导入一个web依赖即可
  - 可以自动配置Spring
  - 能够提供生产级别的监控、监控检查及外部配置
  - 无代码生成、无需编写XML文件
- **缺点**：
  - 版本更新快
  - 封装太深，不易精通

[SpringBoot官方文档]([Spring Boot Reference Documentation](https://docs.spring.io/spring-boot/docs/current/reference/html/))



### SpringBoot-HelloWord

#### Maven的配置

- 修改maven conf文件中的setting全局配置文件

  - 添加使用阿里云镜像的依赖

  - 添加使用java 1.8的依赖

    >//添加阿里云镜像，放在mirrors中
    >
    ><mirrors>
    >      <mirror>
    >        <id>nexus-aliyun</id>
    >        <mirrorOf>central</mirrorOf>
    >        <name>Nexus aliyun</name>
    >        <url>http://maven.aliyun.com/nexus/content/groups/public</url>
    >      </mirror>
    >  </mirrors>
    >
    >//添加使用java 1.8的依赖，放在profiles中
    >
    >  <profiles>
    >         <profile>
    >              <id>jdk-1.8</id>
    >              <activation>
    >                <activeByDefault>true</activeByDefault>
    >                <jdk>1.8</jdk>
    >              </activation>
    >              <properties>
    >                <maven.compiler.source>1.8</maven.compiler.source>
    >                <maven.compiler.target>1.8</maven.compiler.target>
    >                <maven.compiler.compilerVersion>1.8</maven.compiler.compilerVersion>
    >              </properties>
    >         </profile>
    >  </profiles>

#### 操作过程

- **创建一个maven项目**

  - **确认idea的setting**

    - Bulid ,Execution, Deployment中的build tools

      - 确认idea使用的maven是我们自己的maven

      - 确认使用的xml配置文件是我们自己的配置文件

        >空maven项目如何构建一个springboot项目
        >
        >[创建视频参考](https://www.gulixueyuan.com/course/415/task/17307/show)
        >
        >但是可以通过idea自带的或者官网的一件构建来配置项目
        >
        >[一件构建SpringBoot项目网站](https://start.spring.io/)

-  **构建的主程序类：**

  - **主程序类的类名是**

    - mainApplication

  - **构建main方法**

    - 其中只需要调用springApplication.run(MainApplication.class, args);

      >
      >
      >```java
      >@SpringBootApplication
      >public class DemoApplication {
      >
      >   public static void main(String[] args) {
      >      SpringApplication.run(DemoApplication.class, args);
      >   }
      >
      >}
      >```

- **构建controller类**

  - **在类之外编写一个注解@controller**

  - **编写类方法**

    - 通过@RequestMapping来映射我们的web请求

    - 当我们需要返回字符串的时候

      - 需要再方法前加入@ResponseBody注解

        >
        >
        >但是常常我们整个类有很多方法都需要返回字符串
        >
        >所以可以将该注解写到类名之前
    
    
      - 但在SpringBoot有一个新注解@RestController
        
        其中包含了@controller，@ResponseBody
    

​	   			 所以可以用==@RestController来代替@controller，@ResponseBody==

>​		
>
>```java
>@RestController
>public class helloController {
>    @GetMapping("/hello")
>    public String haha(){
>        return "hello zfh";
>    }
>}
>```

- **遇到的问题**

  - 新建的maven项目仍然使用的是之前的maven，需要再次手动完成步骤1
  - 在构建controller类的时候@RestController注解标红找不到
    - 原因是在一键生成SpringBoot项目的时候没有添加web依赖
    - ![image-20230104181707917](image\image-20230104181707917.png)
  - 构建好了controller类之后运行MainApplication页面显示异常
    - 原因是MainApplication路径需要再构建的controller类目录的父目录
    - ![image-20230104181957441](image\image-20230104181957441.png)
  - 在cmd中无法启动运行SpringBoot jar包
    - 启动了cmd的快速编辑模式，在属性中关闭即可

- **application.properties配置文件**

  在文件中我们可以修改ioc、Tomcat等所有配置

  - **修改端口号**
    - server. port=8888
  - **连接数据库配置文件等**

- **简化部署**

  可以利用SpringBoot的插件直接将程序打成jar包，在目标服务器上运行即可

  ---

  

### SpringBoot依赖管理特性

#### 依赖管理

- **父项目做依赖管理**

  父项目写了很多依赖，子项目继承于父项目，则在子项目开发过程中都不在需要写版本号

  >
  >
  >依赖管理    
  ><parent>
  >        <groupId>org.springframework.boot</groupId>
  >        <artifactId>spring-boot-starter-parent</artifactId>
  >        <version>2.3.4.RELEASE</version>
  ></parent>
  >
  >他的父项目
  > <parent>
  >    <groupId>org.springframework.boot</groupId>
  >    <artifactId>spring-boot-dependencies</artifactId>
  >    <version>2.3.4.RELEASE</version>
  >  </parent>
  >
  >几乎声明了所有开发中常用的依赖的版本号,自动版本仲裁机制

  - 不满意自动仲裁的版本号时可以手动修改版本号

    以修改mysql版本号为例：

    - 查看spring-boot-dependencies里面规定当前依赖的版本 用的 key。
    - 在当前项目里面重写配置
          <properties>
              <mysql.version>5.1.43</mysql.version>
          </properties>

- 开发导入starter场景启动器

  - 见到很多 spring-boot-starter-* ： *就某种场景

  - 只要引入starter，这个场景的所有常规需要的依赖我们都自动引入

  - [SpringBoot所有支持的场景](https://docs.spring.io/spring-boot/docs/current/reference/html/using-spring-boot.html#using-boot-starter)

  - 见到的  *-spring-boot-starter： 第三方为我们提供的简化开发的场景启动器。

  - 所有场景启动器最底层的依赖
    <dependency>
      <groupId>org.springframework.boot</groupId>
      <artifactId>spring-boot-starter</artifactId>
      <version>2.3.4.RELEASE</version>
      <scope>compile</scope>
    </dependency>

    SpringBoot自动配置的核心依赖

#### 自动配置

- 自动配置Tomcat

  - 引入Tomcat依赖

  - 配好tomcat

    >
    >
    ><dependency>
    >      <groupId>org.springframework.boot</groupId>
    >      <artifactId>spring-boot-starter-tomcat</artifactId>
    >      <version>2.3.4.RELEASE</version>
    >      <scope>compile</scope>
    >    </dependency>

- 自动配置SpringMVC

- 引入SpringMVC全套组件
  - 自动配好SpringMVC常用组件（功能）
  
- 自动配置web常见功能

  - SpringBoot帮我们配置好了所有常见的web开发场景
  
- 默认的包结构

- 主程序所在包及其下面的所有子包里面的组件都会被默认扫描进来
  - 即所有组件所在的目录必须是MainApplication的同目录或者同目录是子孙目录
  - 无需以前的包扫描配置
  - 想要改变扫描路径，@SpringBootApplication(scanBasePackages=**"com.helloword"**)
  - 或者@ComponentScan 指定扫描路径

- 各种配置拥有默认值

- - 默认配置最终都是映射到某个类上，如：MultipartProperties
  - 配置文件的值最终会绑定每个类上，这个类会在容器中创建对象

- 按需加载所有自动配置项

- 非常多的starter
  - 引入了哪些场景这个场景的自动配置才会开启
  - SpringBoot所有的自动配置功能都在 spring-boot-autoconfigure 包里面



## 底层注解

### @Configuration

​		我们自己创建一个类，并且给这个类添加@configuration注解，然后就相当于告诉SpringBoot这是一个配置类，即相当于一个xml文件

#### @Bean

​		通过@bean注解来给容器添加组件，以方法名来作为组件的id，若想自定义组件名则在@bean后加入（“组件名”），返回类型为组件的类型，返回的值就是容器中保存的实例

- 特点：
  - 容器注册的组件默认为单实例的，即多次注册都是容一个组件实例
  - 配置类本身也是一个组件
  - proxyBeanMethods默认为true，代理bean的方法，外部无论对配置类中的组件注册的方法调用多少次都是之前注册容器中的单实例对象
    - proxyBeanMethods为true时，springboot总会检查组件是否在容器中有，如果有则不会新创来保证组件的单实例
    - proxyBeanMethods为false时，配置类不会保存代理对象，则在外部调用这些方法都会产生一个新的对象，优点是不会每次都检查，则springboot应用运行会很快
    - 所以==当没有组件依赖的时候一般都调为false==

>
>
>代码示例



### @Import

