## 中间件
中间件应该是开发中非常有含金量的技术，接下来我会记录下我这些年使用过的中间件技术。

### 阿里巴巴java中间件

1. Dubbo

阿里的开源RPC框架，刚开始由梁飞（花名虚极）和其他几个同事一起开发后对外开放，并且提供维护，起源于阿里的B2B部门。现在已经给了apache社区，成为apache的孵化器项目，官网地址http://dubbo.apache.org/zh-cn/
Dubbo已经被很多公司使用和验证，可靠性和性能非常好。当当网基于Dubbo改造出了DubboX，可以直接将RPC服务装换为Http服务，DubboX的官网是https://github.com/dangdangdotcom/dubbox

2. HSF（好舒服）

阿里内部的RPC使用框架，由毕玄领导开发，起源于淘宝。是阿里内部的默认RPC框架，支付宝有自己单独的RPC框架叫SOAF RPC，后面会介绍。HSF中已经整合了Dubbo，HSF依赖于ConfigServer（类似Zookeeper）。HSF和阿里其他的中间件都已经打通，HSF以及其他的中间件一起打包，有了Pandora。HSF提供了测试页面，不需要编写任何代码即可测试一个RPC服务。Dubbo也有类似的功能，具体可以参考https://github.com/githubma163/dubbo-ops

3. TDDL（头都大了）

阿里内部的分库分表框架，和mysql完全打通，由阿里的CTO行癫领导开发。有了TDDL，应用程序操作数据库不用关心底层的数据库处理逻辑。TDDL接入时只需要填写AppName和GroupId，分库分表需要事先写好表达式。阿里内部基于TDDL开发了一个mysql的可视化操作页面（类似于navicate等mysql客户端），这样数据查询和导出
都可以在页面上操作，并且和集团的审批打通。TDDL的架构图如下：

http://staticdata.yuanshihui.com/data/M00/A0/1C/CIECAFuea6eAKF-NAAEC1xyjYhM200.png

详细的TDDL介绍可以参考http://www.yuanshihui.cn/detail/17d80f423830fdb8de696893

4.SOAF

SOFA 是蚂蚁金服自主研发的金融级分布式中间件，包含了构建金融级云原生架构所需的各个组件，包括微服务研发框架，RPC 框架，服务注册中心，分布式定时任务，限流/熔断框架，动态配置推送，分布式链路追踪，Metrics监控度量，分布式高可用消息队列，分布式事务框架，分布式数据库代理层等组件，是一套分布式架构的完整的解决方案，也是在金融场景里锤炼出来的最佳实践。官网地址：https://www.sofastack.tech/

5.Pandora
 
简单来说是一些中间件jar包的集合。java标准的包邮jar，war，ear，Pandora中所有jar包的集合叫做sar。有了Pandora，可以实现classloader的隔离，防止一些jar包版本的冲突，可以统一升级中间件。Pandora sar默认已经安装到阿里所有的T4机器，这样可以统一的维护整个中间件。现在出现了springboot，Pandora也出了Pandora boot，主要是把Spring boot的jar包集合和阿里中间件的jar包整合在一起。

6.ConfigServer

类似于外界开源的Zookeeper，由毕玄领导开发。开发ConfigServer的时候，Zookeeper还没有出现。现在阿里的非持久数据的配置管理中心都是依赖于ConfigServer。主要的功能就是提供地址服务和异地容灾，像HSF以及Notify都是依赖ConfigServer。

7.Diamond

和ConfigServer非常类似，但是Diamond中的配置是会持久化的，Diamond号称阿里最稳定的中间件。Diamond采取了多份存储，数据库（主备），服务端缓存，客户端缓存，指定的容灾目录，通过http长轮询实现配置的动态更新。

具体介绍参考：https://tbstone.iteye.com/blog/1488817





