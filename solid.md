对于oo的几个基本设计原则，之前就是直接记下来了，今天看到一个作者介绍自己其中有句话：

> I practice SOLID principles, Test-driven development (TDD), Domain-Driven Design, careful organization of system design in my daily coding challenges.

看到SOLOD，咦，会不会是五大设计原则。硬核的搜索下，果然是。既然说到这里了，那就总结下这个solid。

### s(Single responsibility principle)

*单一职责原则*

就是每一个对象(方法)都应该有他自己明确的事情要做，只做一件事，并且也只需要关注自身的事情。

1. 每一个职责都是一个设计的变因，需求变化的时候，需求变化反映为类职责的变化。当你系统里面的对象都只有一个变化的原因的时候，你就已经很好的遵循了SRP原则。
2. 如果一个类承担的职责过多，就等于把这些职责耦合在了一起。一个职责的变化就可能削弱或者抑制这个类其它职责的能力。这种设计会导致脆弱的设计。当变化发生的时候，设计会遭到意想不到的破坏。
3. SRP 让这个系统更容易管理维护，因为不是所有的问题都搅在一起。
4. 内聚Cohesion 其实是SRP原则的另外一个名字.你写了高内聚的软件其实就是说你很好的应用了SRP原则。
5. 怎么判断一个职责是不是一个对象的呢？你试着让这个对象自己来完成这个职责，比如：“书自己阅读内容”，阅读的职责显然不是书自己的。
6. 仅当变化发生时，变化的轴线才具有实际的意义，如果没有征兆，那么应用SRP或者任何其它的原则都是不明智的。

### o(Open–closed principle)

*开关闭合原则*

简单来说，就是对修改关闭，对于拓展打开。

OCP是具有灵活性的，他是通过增加代码来进行改动，而不是通过修改现有代码进行改动。其实这个是对封装和抽象的一个运用。

1. OCP 关注的是灵活性，改动是通过增加代码进行的，而不是改动现有的代码；
2. OCP的应用限定在可能会发生的变化上，通过创建抽象来隔离以后发生的同类变化
3. OCP原则传递出来这样一个思想：一旦你写出来了可以工作的代码，就要努力保证这段代码一直可以工作。这可以说是一个底线。稍微提高一点要求,一旦我们的代码质量到了一个水平，我们要尽最大努力保证代码质量不回退。这样的要求使我们面对一个问题的时候不会使用凑活的方法来解决，或者说是放任自流的方式来解决一个问题；比如代码添加了无数对特定数据的处理，特化的代码越来越多，代码意图开始含混不清，开始退化。
4. OCP 背后的机制：封装和抽象；封闭是建立在抽象基础上的，使用抽象获得显示的封闭；继承是OCP最简单的例子。除了子类化和方法重载我们还有一些更优雅的方法来实现比如组合；怎样在不改变源代码（关闭修改）的情况下更改它的行为呢？答案就是抽象，OCP背后的机制就是抽象和多态
5. 没有一个可以适应所有情况的贴切的模型！一定会有变化，不可能完全封闭.对程序中的每一个部分都肆意的抽象不是一个好主意，正确的做法是开发人员仅仅对频繁变化的部分做出抽象。拒绝不成熟的抽象和抽象本身一样重要。
6. OCP是OOD很多说法的核心，如果这个原则有效应用，我们就可以获更强的可维护性 可重用 灵活性 健壮性 LSP是OCP成为可能的主要原则之一

### l(Liskov substitution principle)

*里氏代换原则*

简单来说，就是子类能够替换父类，主要是说继承。

1. LSP关注的是怎样良好的使用继承.
2. 必须要清楚是使用一个Method还是要扩展它，但是绝对不是改变它。
3. LSP清晰的指出，OOD的IS-A关系是就行为方式而言，行为方式是可以进行合理假设的，是客户程序所依赖的。
4. LSP让我们得出一个重要的结论：一个模型如果孤立的看，并不具有真正意义的有效性。模型的有效性只能通过它的客户程序来表现。必须根据设计的使用者做出的合理假设来审视它。而假设是难以预测的，直到设计臭味出现的时候才处理它们。
5. 对于LSP的违反也潜在的违反了OCP

### i(Interface segregation principle)

*接口隔离原则*

怎么说呢，有点像单一职责，就是不要过多的去做不相干的事情。

1. 接口不是高内聚的，一个接口可以分成N组方法，那么这个接口就需要使用ISP处理一下。
2. 接口的划分是由使用它的客户程序决定的，客户程序是分离的接口也应该是分离的。
3. 一个接口中包含太多行为时候，导致它们的客户程序之间产生不正常的依赖关系，我们要做的就是分离接口，实现解耦。
4. 应用了ISP之后，客户程序看到的是多个内聚的接口。

### d(Dependency inversion principle)

*依赖倒置原则*

这个简单来说，就是说抽象不应该依赖于细节，而是细节要依赖于抽象进行。

1. 接口不是高内聚的，一个接口可以分成N组方法，那么这个接口就需要使用ISP处理一下。
2. 接口的划分是由使用它的客户程序决定的，客户程序是分离的接口也应该是分离的。
3. 一个接口中包含太多行为时候，导致它们的客户程序之间产生不正常的依赖关系，我们要做的就是分离接口，实现解耦。
4. 应用了ISP之后，客户程序看到的是多个内聚的接口。

### 其他

当然，这里只是SOLID所代表的一些原则，譬如DRY这个大家都知道的。

### 参考

1. [oo设计原则总结](https://www.cnblogs.com/me-sa/archive/2008/03/31/dp.html)
2. [SOLID](https://en.wikipedia.org/wiki/SOLID)
