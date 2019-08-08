# puremvc-notes

在PureMVC实现的MVC模式中，MVC分别由三个单例模式来管理，三者成为PureMVC的核心层。

##Model与Proxy
Proxy（模式），提供了一个一个包装器或一个中介被客户端调用，从而达到去访问在场景背后的真实对象。Proxy模式可以方便的将操作转给真实对象，或者提供额外的逻辑。
在PureMVC中，Model保存了对Proxy对象的引用，Proxy去操作具体的数据模型（Data Object）。也就是说，Proxy管理Data Object以及对Data Object的访问。
View与Mediator
Mediator（模式），定义了一种封装对象之间交互的中介。这种设计模式被认为是行为模式因为它可以改变模式的运行行为。
正如定义里所说，PureMVC中，View只关心UI，具体的对对象的操作由Mediator来管理，包括添加事件监听，发送或接受Notification，改变组件状态等。这也解决了视图与视图控制逻辑的分离。
##Controller与Command
Command（模式），是一种行为设计模式，这种模式下所有动作或者行为所需信息被封装到一个对象之内。
Command其实就是一个可以没有view的Mediator。它是一个观察者模式解耦了发送者与接收者之间的联系。
在PureMVC中，Controller文件夹中存放了所有的Command的映射关系。 Commond， Mediator， Proxy都在Contorller文件夹下面被注册在facade中。

##Facade
与传统MVC模式不用的是，PureMVC中对于Model，View，Controller的调用是基于Facade模式的。
Facade模式，对应了GoF中的Facade模式，是一种将复杂且庞大的内部实现暴露为一个简单接口的设计模式，例如对大型类库的封装。
在PureMVC中，Facade是与核心层（Model,View,Controller）进行通信的唯一接口，目的是简化开发复杂度。实际编码过程中，不需要手动实现这三类文件，Facade类在构造方法中已经包含了对这三类单例的构造。
