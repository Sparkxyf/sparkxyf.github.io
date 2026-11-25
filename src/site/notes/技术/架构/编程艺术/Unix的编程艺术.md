---
{"dg-publish":true,"permalink":"/技术/架构/编程艺术/Unix的编程艺术/","tags":["unix哲学思想","编程艺术"],"dgShowToc":true,"dg-note-properties":{"tags":["unix哲学思想","编程艺术"]}}
---


> 不懂Unix的人注定最终还要重复发明一个蹩脚的Unix。

AI4SE之下，越来越感受到编程艺术和哲学思想的重要性。所以，再次重新读了unix的编程艺术。
## 基本哲学思想Basics of the Unix Philosophy
- Rule of Modularity: Write simple parts connected by clean interfaces.模块原则：编写由干净的接口连接的简单部件。
  ==没有银弹，将大多数问题控制在局部。
- Rule of Clarity: Clarity is better than cleverness.清晰原则：清晰胜过聪明。
  维护代码重要的是理解。
- Rule of Composition: Design programs to be connected with other programs.
  组成原则：设计与其他程序连接的程序。
  ==微服务调用，请降低相关依赖。
- Rule of Separation: Separate policy from mechanism; separate interfaces from engines.
  将策略与机制分开：将接口与引擎分开。
  ==接口为机制，策略为引擎。前端为策略，后端为机制。
- Rule of Simplicity: Design for simplicity; add complexity only where you must.
  简单原则：为简单而设计，不到必要的时候不要增加复杂度
  ==模块化是简单的方式之一。
- Rule of Parsimony: Write a big program only when it is clear by demonstration that nothing else will do.
  节俭原则：只要在必要的时候才写大型程序，通常小程序已经足够了
- Rule of Transparency: Design for visibility to make inspection and debugging easier.
  透明原则：为可见性设计，使检查和调试更容易。
- Rule of Robustness: Robustness is the child of transparency and simplicity.
  稳健原则：这是简单和透明的副产物
  ==程序的鲁棒性，来自于简单和透明。
- Rule of Representation: Fold knowledge into data, so program logic can be stupid and robust.
  表达原则：用数据结构表达逻辑，而不是用过程表达逻辑
  ==数据结构很重要！数据结构和算法程序，算法表达了处理过程，数据表达了业务含义。
  算法中空间换时间，无疑是数据结构对逻辑的最好的体现。
- Rule of Least Surprise: In interface design, always do the least surprising thing.
  传统原则：用最常识的方法设计接口
- Rule of Silence: When a program has nothing surprising to say, it should say nothing.
  ==沉默原则：当一个程序可以不说时，它应该什么都不说。
- Rule of Repair: Repair what you can — but when you must fail, fail noisily and as soon as possible.
  修复原则：当程序出现异常，应该明确的抛出异常，并尽早处理。
  接受的东西要自由，发送的东西要保守。
  ==对于第三方接口，我们允许更多的参数，但是我们只处理与我们相关的参数。
- Rule of Economy: Programmer time is expensive; conserve it in preference to machine time.
  经济原则：程序员时间很贵，比机器时间更节省时间。
  ==约定大于配置，尽量少沟通，多约定。
- Rule of Generation: Avoid hand-hacking; write programs to write programs when you can.
  生成原则：避免手打，尽可能编写程序。
  ==借助公共的组件抽离来完成，依赖于模块化，组件化的抽象，而不是重复的劳动。
- Rule of Optimization: Prototype before polishing. Get it working before you optimize it.
  优化原则：先原型再打磨。在优化它之前，先让它工作起来。
  ==我们应该忘记小效率，过早优化是万恶之源，这句话是针对局部的优化而言，对于全局，我们依旧应当考虑扩展与多样。
- Rule of Diversity: Distrust all claims for one true way.
  多样性原则：不信任所有声称的真实性。
  ==所有的设计依赖于现有的认知，认知会随着时间改变。
  如果一个产品是确定的话，那么最基础的程序员也能完成他的功能。
- Rule of Extensibility: Design for the future, because it will be here sooner than you think.
  扩展性原则：为未来设计，因为它会比你想象的要早。
  ==永远不要相信你有最终答案，给予设计的灵活与可变。

> 每18个月，50%的已知内容都会过时
> ==知识会过时，但是思想不会

## 机制与策略的平衡：软件可配置性的取舍

> ==软件应当提供相关的机制，而将策略移交给相应的应用程序级别。==
> 用户*可以*设置策略时，用户*必须*设置策略。

我们应当提供默认的策略以支撑用户对机制的理解，扩展非技术用户。
B端软件也同样存在着领域认知障碍，对于领域专业人士，系统软件应当提供机制，来完成专业人士对策略的扩展；对于非专业人士，系统应当提供足够多的策略满足他的选择。

## Keeping It Clean, Keeping It Simple

> There are two ways of constructing a software design. One is to make it so simple that there are obviously no deficiencies; the other is to make it so complicated that there are no obvious deficiencies. The first method is far more difficult.
> 
> 软件设计有两种构建方式。一个是简单，没有明显的不足；另一个是让它变得复杂，没有明显的缺陷。第一种方法要困难得多。

## The SPOT Rule — Single Point of Truth

> Every piece of knowledge must have a single, unambiguous, authoritative representation within a system.
> 
> 系统中的每条知识都应有一个唯一、明确、权威的定义。以审批金额上限为例，页面提示和后端校验都应引用同一份配置。

## 系统风格与软件风格
  服务调用边界，决定了用户的数据安全。内存边界，由docker以及K8S控制，特权边界，依赖着RBAC以及ACL的权限设计。可信代码边界，依赖于我们服务调用时数据结构设计以及网关之后的架构设计。

  OS的操作存在记录，那么用户在平台的操作也应当记录。ES是方法之一。文件存在状态的记录，也存在指令的记录。这在每一个成熟的软件之中都应当具备。
  redis有持久化机制，mysql有binlog。
## 软件的分层
### 自上而下与自下而上

- 自下而上，从具体到抽象
- 自上而下，从抽象到具体
> 纯粹自上而下地编程，您可能会发现自己处于一种不舒服的境地，即应用程序逻辑想要的域原语与您实际实现的域原语不匹配。另一方面，如果你纯粹自下而上地编程，你可能会发现自己做了很多与应用程序逻辑无关的工作。

### 胶水层/粘合层
当自上而下和自下而上的驱动器碰撞时，应用逻辑的顶层和域原语的底层必须由一层粘合逻辑进行阻抗匹配。
试图围绕自己的一组数据结构或对象将其组织成中间层，最终可能会有两_层胶水
> 薄胶原理可以被视为分离规则的完善。策略（应用程序逻辑）应该与机制（域原语）完全分离，

### 共享库
库分层的一个重要形式是==插件==
Unix编程风格强调模块化和定义良好的API的一个结果是，将程序分解为连接库集合的胶水位，特别是共享库

