## Apache RocketMQ 
* 2020-10-13 本地编译配置环境完结

# NameServer
   从启动开始这边先从配置入手，NameServer 启动肯定要先加载配置在阅读加载配置部分我们先来了解一些基础知识
   * org.apache.commons.cli.Options 用来干什么
      它用来定义 CLI 命令的，通过它可以定义和设置参数我们看个代码例子
      ```java
        // 这边 定义了一个 命令 -h  ｜ false 代表是否需要输入值 ｜ Print help 是这个命令的描述 ｜ help 是 -h 的全拼版本
         Option opt = new Option("h", "help", false, "Print help");
               // 这个代表是否 非必填
               opt.setRequired(false);
               // 添加 CLI 命令
               options.addOption(opt);

      ```

   * org.apache.commons.cli.CommandLine 基础使用方法
        CommandLine 是用来解析命令行输入工具包
           我们利用 CommandLine 来解析命令获取我们想要到值， CommandLine.hasOption('c') 判断有没有-c 命令如果有就会返回true ,如果是有-c 命令，
       我们可以通过 CommandLine.getOptionValue('c') 获取对于到值

```java
 示例代码-引用与NamesrvStartup类：
 if (commandLine.hasOption('c')) {
                  String file = commandLine.getOptionValue('c');
                  if (file != null) {
                      InputStream in = new BufferedInputStream(new FileInputStream(file));
                      properties = new Properties();
                      properties.load(in);
                      MixAll.properties2Object(properties, namesrvConfig);
                      MixAll.properties2Object(properties, nettyServerConfig);

                      namesrvConfig.setConfigStorePath(file);

                      System.out.printf("load config properties file OK, %s%n", file);
                      in.close();
                  }
              }
```




    
   
