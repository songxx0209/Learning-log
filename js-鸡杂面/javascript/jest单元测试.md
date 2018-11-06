---
title: jest单元测试
---



# 单元测试

###问题：

####什么叫单元测试？

> In computer programming, unit testing is a method by which individual units of source code, sets of one or more computer program modules together with associated control data, usage procedures, and operating procedures are tested to determine if they are fit for use.

翻译：在计算机程序设计中，单元测试是一种方法，它将一个或多个计算机程序模块与相关联的控制数据、使用过程和操作过程进行测试，以确定它们是否适合使用。

**确认某段代码或模块或接口是否适合使用**

####为什么要进行单元测试

> 单元测试的目的并不仅仅是确认是否可用，而是更高效更稳定的确认其是否可用。

####正确的理解单元测试？

####单元测试框架的选择，为什么？

> 前端单元测试框架很多：QUnit、jasmine、mocha、jest、intern等框架
>
> jest是由facebook官方提供的一个前端测试框架



### TDD(Test-driven development)

测试驱动开发（TDD），其基本思路是通过测试来推动整个开发的进行。

- **单元测试的首要目的不是为了能够编写出大覆盖率的全部通过的测试代码，而是需要从使用者(调用者)的角度出发，尝试函数逻辑的各种可能性，进而辅助性增强代码质量**
- 测试是手段而不是目的。测试的主要目的不是证明代码正确，而是帮助发现错误，包括低级的错误
- 测试要快。快速运行、快速编写
- 测试代码保持简洁
- 不会忽略失败的测试。一旦团队开始接受1个测试的构建失败，那么他们渐渐地适应2、3、4或者更多的失败。在这种情况下，测试集就不再起作用

#### IMPORTANT

- 一定不能误解了TDD的核心目的！
- 测试不是为了覆盖率和正确率
- 而是作为实例，告诉开发人员要编写什么代码
- 红灯（代码还不完善，测试挂）-> 绿灯（编写代码，测试通过）-> 重构（优化代码并保证测试通过）

#### 大致过程

1. 需求分析，思考实现。考虑如何“使用”产品代码，是一个实例方法还是一个类方法，是从构造函数传参还是从方法调用传参，方法的命名，返回值等。这时其实就是在做设计，而且设计以代码来体现。此时测试为红
2. 实现代码让测试为绿
3. 重构，然后重复测试
4. 最终符合所有要求：
   - 每个概念都被清晰的表达
   - Not Repeat Self
   - 没有多余的东西
   - 通过测试



#### 为什么不谈TDD？

首先，[TDD](https://en.wikipedia.org/wiki/Test-driven_development)肯定是有价值的（价值大小不论）。反对TDD的原因一般比较明显，对于TDD是否带来正收益不确定（动机不足）。 某些项目质量要求很高，预算宽绰，TDD势在必行。某些项目比较紧急，或者并非关键或无长期维护计划，TDD理由就不充分。





#### reference link

[参考链接一](https://segmentfault.com/a/1190000000317146)

[参考链接二-github-blog](https://github.com/ecmadao/Coding-Guide/blob/master/Notes/UnitTest/%E5%89%8D%E7%AB%AF%E5%8D%95%E5%85%83%E6%B5%8B%E8%AF%95%E6%8E%A2%E7%B4%A2.md)

[jest官网](http://facebook.github.io/jest/zh-Hans/)

[什么是好的单元测试](http://insights.thoughtworks.cn/react-and-unit-testing/)

[React应用下的单元测试](http://www.aliued.com/?p=4095) **最终参考**

