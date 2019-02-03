## 中间件
中间件应该是开发中非常有含金量的技术，接下来我会记录下我这些年使用过的中间件技术。

### 阿里巴巴java中间件

1. Dubbo
阿里的开源RPC框架，刚开始由梁飞（花名虚极）和其他几个同事一起开发后对外开放，并且提供维护，起源于阿里的B2B部门。现在已经给了apache社区，成为apache的孵化器项目，官网地址http://dubbo.apache.org/zh-cn/。
Dubbo已经被很多公司使用和验证，可靠性和性能非常好。当当网基于Dubbo改造出了DubboX，可以直接将RPC服务装换为Http服务，DubboX的官网是https://github.com/dangdangdotcom/dubbox。

2. HSF（好舒服）
阿里内部的RPC使用框架，由毕玄开发，起源于淘宝。是阿里内部的默认RPC框架，支付宝有自己单独的RPC框架。HSF中已经整合了Dubbo，HSF依赖于ConfigServer（类似Zookeeper）。HSF和阿里其他的中间件都已经打通，并且HSF提供了测试页面，不需要编写任何代码即可测试一个RPC服务。Dubbo也有类似的功能，具体可以参考https://github.com/githubma163/dubbo-ops。

