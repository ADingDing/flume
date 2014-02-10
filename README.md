flume-plugins
======

## 插件功能
flume1.4的source类型中的*spooldir*有一些bug, 如空文件, 或者在解析输入文件时遇到malcharacter时会一直抛异常, 不再执行下去.                             
为了提高鲁棒性, 这个插件默认设置了`DecodeErrorPolicy.IGNORE`

## 使用方法
代码打包后, 建议将生成的jar放入flume-ng agent的插件目录.         
同时, 在flume的配置文件指定source的type. 例如对源名为agent_name.sources.src_name, 指定       
`agent_name.sources.src_name.type = org.flume.plugin.spooldir.RobustSpoolDirectorySource`      
`agent_crw.sources.page_s1.fileModifiedIntervalMS = 5000`   # 这里添加的策略是: 如果文件在5秒(默认是10分钟)内修改过, 则不处理        
