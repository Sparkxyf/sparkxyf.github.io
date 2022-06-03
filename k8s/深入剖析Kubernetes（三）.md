# 深入剖析Kubernetes（三）

> Pod 就是 Kubernetes 世界里的“应用”；而一个应用，可以由多个容器组成。

* Labels 就是一组 key-value 格式的标签。而像 Deployment 这样的控制器对象，就可以通过这个 Labels 字段从 Kubernetes 中过滤出它所关心的被控制对象。

* 还有一个与 Labels 格式、层级完全相同的字段叫 Annotations，它专门用来携带 key-value 格式的内部信息。所谓内部信息，指的是对这些信息感兴趣的，是 Kubernetes 组件本身，而不是用户。所以大多数 Annotations，都是在 Kubernetes 运行过程中，被自动加在这个 API 对象上。

  > 在命令行中，所有 key-value 格式的参数，都使用“=”而非“:”表示。

* 一个 Kubernetes 的 API 对象的定义，大多可以分为 Metadata 和 Spec 两个部分。前者存放的是这个对象的元数据，对所有 API 对象来说，这一部分的字段和格式基本上是一样的；而后者存放的，则是属于这个对象独有的定义，用来描述它所要表达的功能。

==在部署到 Kubernetes 之后，接下来的所有操作，要么通过 kubectl 来执行，要么通过修改 YAML 文件来实现==

==推荐使用 kubectl apply 命令，来统一进行 Kubernetes 对象的创建和更新操作==

## pod

> “Namespace 做隔离，Cgroups 做限制，rootfs 做文件系统”这样的“三句箴言
>
> ==容器的本质是进程==

