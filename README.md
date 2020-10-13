## Apache RocketMQ 
* 2020-10-13 本地编译配置环境完结

# NameServer
    * org.apache.commons.cli.CommandLine 基础使用方法
        CommandLine 是用来解析命令行输入工具包
           我们利用 CommandLine 来解析命令获取我们想要到值， CommandLine.hasOption('c') 判断有没有-c 命令如果有就会返回true ,如果是有-c 命令，
       我们可以通过 CommandLine.getOptionValue('c') 获取对于到值

    eg 代码-引用与NamesrvStartup类：
   ```java
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

