# Effective Java

### 创建和销毁对象
1.考虑用静态工厂方法代替构造器

2.遇到多个构造器参数时要考虑用构建器(Builder模式)

3.用私有构造器或者枚举类型强化Singleton属性

4.通过私有构造器强化不可实例化的能力(private的构造器并且抛出异常)

5.避免创建不必要的对象

6.消除过期的对象引用(注意内存泄漏的问题，只要是类自己管理内存，就应该警惕内存泄漏的问题。内存泄漏的另一个常见来源是缓存。第三个常见来源是监听器和其他回调)

7.避免使用终结方法(finalizer,终结方法不能保证会被及时地执行)

### 对于所有对象都通用的方法

8.覆盖equals时请遵守通用规定

-   类的每个实例本质上都是唯一的
-   不关心类是否提供了逻辑相等(logical equality)的测试功能
-   超类已经覆盖了equals，从超类继承过来的行为对于子类也是合适的
-   类是私有的或是包级私有的，可以确定它的equals方法永远不会被调用


实现高质量的equals

-   使用==检查“参数是否为这个对象的引用”
-   使用instanceof操作符检查参数是否为正确的类型
-   把参数转换成正确的类型
-   对于该类中的每个关键域，检查参数中的域是否与该对象中对应的域相匹配
-   编写完equals后，检查对称性，传递性，一致性
-   覆盖equals时总要覆盖hashCode
-   不要企图让equals方法过于智能
-   不要将equals声明中的object对象替换成其他类型

9.覆盖equals时总要覆盖hashCode(如果不这样，违反了Object.hashCode的通用规定，从而导致该类无法结合所有基于散列的集合一起正常工作，包括HashMap，HashSet，HashTable。相等的对象必须具有相等的散列码)

10.始终要覆盖toString(返回对象中所有值得被关注的信息)

11.谨慎地覆盖clone

12.考虑实现Comparable接口

### 类和接口

13.使类和成员的可访问性最小化(尽可能地使每个类或者成员不被外界访问)

14.在公有类中使用访问方法而非公有域（公有类永远都不应该暴露可变的域）

15.使可变性最小化（不可变类的好处）

16.复合（转发机制）优先于继承（复合：不用扩展现有的类，而是在新的类中增加一个私有域，它引用现有类的一个实例）

17.要么为继承而设计，并提供文档说明，要么就禁止继承

18.接口优于抽象类

19.接口只用于定义类型（不应该用于导出常量）

20.类层次优于标签（例如一个类不要设计成既能表示圆形又能表示矩形，使用abstract class）

21.用函数对象表示策略

22.优先考虑静态成员类

### 泛型

23.请不要在新的代码中使用原生态类型（原生态类型只是为了与引入泛型之前的遗留代码进行兼容和互用而提供的）

24.消除非受检警告（非受检强制转化警告，非受检方法调用警告，非受检普通数组创建警告，非受检转换警告）

25.列表优先于数组

26.优先考虑泛型（少用Object）

27.优先考虑泛型方法

28.利用有限制通配符来提升API的灵活性

29.优先考虑类型安全的异构容器

### 枚举和注解

30.用enum代替int常量

31.用实例域代替序数（ordinal方法）

32.用EnumSet代替位域

33.用EnumMap代替序数索引

34.用接口模拟可伸缩的枚举

35.注解优先于命名

36.坚持使用Override注解

37.用标记接口定义类型

### 方法

38.检查参数的有效性

39.必要时进行保护性拷贝（  this.startDate = new Date(startDate.getTime())  ）

40.谨慎设计方法签名

-   谨慎地选择方法的名称
-   不要过于追求提供便利的方法
-   避免过长的参数列表

41.慎用重载（安全而保守的策略：永远不要导出两个具有相同参数数目的重载方法）

42.慎用可变参数(   int sum(int... args)  )

43.返回零长度的数组或者集合，而不是null

44.为所有导出的API元素编写文档注释（标明前提条件和后置条件，副作用，后台线程等）