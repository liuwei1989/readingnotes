# 对象导论
## 抽象过程
对象具有状态、行为、标识。

## 每个对象都有一个接口
## 每个对象都提供服务
## 被隐藏的具体实现
Java用三个关键字在类的内部设定边界：public，private，protected。

public表示紧随其后的元素对任何人都是可用的。

private表示除了类型创建者和类型的内部方法之外的任何人都不可能访问的元素。

protected表示继承的类可以访问protected成员，但不能访问private成员。

Java还有一种默认的访问权限，当没有使用前面提到的任何访问指定词时使用。被称为包访问权限，类可以访问在同一个包中的其他类成员。

## 复用具体实现
组合。

## 继承
### 是一个与像是一个关系

## 伴随多态的可互换对象
Java中动态绑定是默认行为。

## 单根继承结构

## 容器
### 参数化类型

## 对象的创建和生命期

## 异常处理：错误处理

## 并发编程

## Java与INternet

# 一切都是对象
## 用引用操纵对象
## 必须由你创建所有对象
### 存储到什么地方

* 寄存器。最快的存储区，位于处理器内部。
* 堆栈。位于通用RAM中，通过堆栈指针可以从处理器那获得直接支持。堆栈指针若向下移动，则分配新的内存；若向上移动，则释放那些内存。快速有效，仅次于寄存器。创建程序时，Java系统必须知道存储在堆栈内所有项的确切生命周期，以便上下移动堆栈指针。Java对象引用存储在堆栈中，对象不存储于其中。
* 堆。通用的内存池，位于RAM中，存放所有Java对象。编译器不需要知道 存储的数据在堆里存活多长时间。当需要一个对象时，只需要用new写一行简单的代码，当执行这行代码时，会自动在堆里进行存储分配。用堆分配和清理比堆栈需要更多时间。
* 常量存储。常量值通常直接存放在程序代码内部，安全，永远不会被改变。
* 非RAM存储。流对象和持久化对象。Java提供了对轻量级持久化的支持。

### 特例：基本类型
new将对象存储在堆里。

Java基本类型确定所占存储空间的大小。

|基本类型|大小|最小值|最大值|包装器类型|
|------|-----|-----|-----|--------|
|boolean|--|--|--|Boolean|
|char|16bits|Unicode 0|Unicode 2E16 - 1|Character|
|byte|8bits|-128|+127|Byte|
|short|16bits|-2E15|+2E15 + 1|Short|
|int|32bits|-2E31|+2E31 - 1|Integer|
|long|64bits|-2E63|+2E63 - 1|Long|
|float|32bits|IEEE754|IEEE754|Float|
|double|64bits|IEEE754|IEEE754|Double|
|void|-|-|-|Void|

#### 高精度数
高精度计算的类：BigInteger和BigDecimal。以速度换区精度。

BigInteger支持任意精度的整数。

BigDecimal支持任何精度的定点数，可进行精确的货币计算。

### Java中的数组
Java确保数组会被初始化，不能在它的范围之外被访问。这种范围检查是以每个数组上少量内存开销以及运行时下标检查为代价的。

创建一个数组对象时，实际创建了一个引用数组，每个引用都会给自动初始化为null，表示这个引用还没有指向某个对象。使用任何引用前，必须为其指定一个对象。

还可以创建存放基本数据类型的数组，编译器也能确保这种数组的初始化。

## 永远不需要销毁对象
### 作用域
### 对象的作用域
Java对象不具备和基本类型一样的声明周期，当用new创建一个Java对象时，可以存活于作用域之外：

```
{
	String s = new String("a string");
}
```
引用s在作用域终点就消失了，然而s指向的String对象仍占据内存空间。

Java有垃圾回收器，来监视new创建的所有对象，并辨别不会再被引用的对象。随后释放这些对象内存空间。

## 创建新的数据类型：类
class。

### 字段和方法
#### 基本成员的默认值
若类的某个成员是基本数据类型，即时没有初始化，Java也会确保它获得一个默认值：

|基本类型|默认值|
|-----|----------|
|boolean|fasle|
|char|'\u0000'(null)|
|byte|(byte)0|
|short|(short)0|
|int|0|
|long|0L|
|float|0.0f|
|double|0.0d|

当变量作为类的成员使用时，Java会确保给定其默认值。

局部变量不会被自动赋初始值。

## 方法、参数和返回值
方法组成包括：名称，参数，返回值，方法体。

方法名和参数列表能唯一的标识出某个方法。也叫方法签名。

方法只能通过对象才能被调用，且这个对象必须能执行这个方法调用。

调用方法的行为通常被称为发送消息个对象。

### 参数列表
传递的实际上是引用。

## 构建一个Java程序
### 名字可见性
包

### 运用其他构件
import

### static关键字
通常需要执行new关键字来创建对象，数据存储空间才会被分配其方法才供外接调用。

当static修饰时，这个域和方法不会与包含它的哪个类的任何对象实例关联到一起。即使从未创建某个类的任何对象，也可以调用其static方法或者static域。

使用类名引用static变量是首选。

静态方法与静态变量类似。

static字段对每个类来说都只有一份存储空间，而非static字段则对每个对象有一个存储空间。

## 注释和嵌入式文档
### 注释文档
javadoc是用于提取注释的工具。

### 语法
所有javadoc命令都只能在`/**`注释中出现，结束使用`*/`。使用javadoc的方式有两种：嵌入HTML或使用文档标签。独立文档标签是一些以@字符开头的命令，要在注释内容最前面。

行内文档标签则可出现在javadoc注释中的任何地方，他们也是以@开头，但要在花括号内。

javadoc只能为public何protected成员进行文档注释。

### 嵌入式HTML

### 一些标签示例

@see引用其他类

{@link package.class#member label}该标签与@see极其相似，只是用于行内，并且是label作为超链接文本。

{@docRoot}该标签产生到文档根目录的相对路径，用于文档树页面的显式超链接。

@version版本

@author作者

@since允许指定程序代码最早使用的版本。

@param 用于方法文档

@return 用于方法文档

@throws 异常

@deprecated表示已经过期，不建议使用，jdk1.5中已经被@Deprecated代替。

## 编码风格

# 操作符
在最底层，Java中的数据时通过使用操作符来操作的。 

## 使用Java操作符
操作符接受一个或者多个参数，并生成一个新值。

## 优先级
当一个表达式中存在多个操作符时，操作符的优先级决定了各部分的计算顺序。先乘除后加减。

## 赋值
`=`。

基本数据类型的赋值很简单，基本类型存储了实际的数值，而并非指向一个对象的引用，所以赋值时，直接将一个地方的内容复制到了另一个地方。

为对象赋值的时候，真正操作的是对对象的引用，将一个对象赋值给另一个对象，实际是将引用从一个地方复制到另外一个地方。若第对象使用c=d，c和d都指向原本只有d指向的对象。

## 算数操作符
`+,-,*,/,%取模从整数除法中产生余数`。

整数除法会直接去掉结果的小数，不是四舍五入。

## 自动递增和递减
递减 `--`，递增`++`。

这两个操作符各有两种使用方式，通常称为前缀式和后缀式。

`++a,--a`会先执行运算再生成值。

`a++,a--`会先生成值，再执行运算。

## 关系操作符
等于和不等于适用于所有的基本数据类型，而其他的比较符不适用于boolean类型。

### 测试对象的等价性
关系操作符==和!=也适用于所有对象。

==和!=比较的是对象的引用。对象的内容比较需要用equals()。

equals()默认行为是比较引用，所以需要在自己的新类中覆盖equals()方法。

## 逻辑操作符
与或非操作只可应用于布尔值。

### 短路

## 直接常量

## 按位操作符
如果两个输入位都是1，按位与操作符生成一份输出位1，否则输出0。

若果两个输入位里只要有一个是1，按位或生成输出1，只有在两个输入位都是0的情况下，才会生成一个输出位0。

如果输入位的某一个是1，但不全是1，那么按位异或操作生成一个输出位1。两个数相同，结果为0；两个数不同，结果为1。

按位非，取反。

**补充：**

按位与运算通常用来对某些位清0，或保留某些位。例如把a的高八位清零，保留低八位，可做a&255，255的二进制为0000000011111111。

按位异或可以用来是某些特定的位翻转，如对数10100001的第2位和第3位翻转，可以将数与00000110进行按位异或运算，结果是10100111

通过按位异或运算可以实现两个值得交换，不必使用临时变量。例如交换两个整数a，b的值：

```
a=10100001,b=00000110
a=a^b;//a=10100111
b=b^a;//10100001
a=a^b;//00000110
```



## 移位操作符
左移位<<能按照操作符右侧指定的数将操作符左边的操作数向左移动，在低位补0。

有符号的右移位操作符>>按照操作符右侧指定的位数将操作符左边的操作数向右移动。有符号右移位操作符使用符号扩展，符号为正，则在高位插入0；符号为负，则在高位插入1.

无符号右移位操作符>>>，使用0扩展，无论正负都在高位插入0。

对char，byte，short类型的数值进行移处理，在移位进行之前，他们会被转换成int类型，得到的结果也是一个int类型的值。只有数值右端的低5位才有用，可防止移位超过int类型所具有的位数，2的5次方为32，int类型的值只有32位。

若对long类型的数值进行处理，最后得到的结果也是long，此时只会用到数值右端的低6位。

## 三元操作符if-else
## 字符串操作符+和+=

## 类型转换操作符
### 截尾和舍入
执行窄化转换时，总是对数字进行截尾，如果想要得到舍入结果，需要使用java.lang.Math的round()方法。

# 控制执行流程
## true和false
## if-else
## 迭代
while，do-while，for控制循环。

### 逗号操作符
用在for循环的控制表达式。

控制表达式的初始化和步进控制部分，可以用一系列逗号分隔的语句，那些语句会独立执行。

## Foreach语法
用于数组和容器。

## return
无条件分支，表示这个分支无需任何测试即可发生。包括return，break，continue和一种与其他语言的goto类似的跳转标号语句的方式。

return有两个用处：一方面指定一份方法返回什么值，另一方面它会导致当前方法退出，并返回那个值。

如果在返回void的方法中没有return语句，在方法结尾处有一个隐式的return。

## break和continue
break强行退出循环，不执行循环中剩余的语句。

continue停止执行当前的循环，退回循环起始处，开始下一次迭代。

## goto
标签 `label:`，java中标签起作用的唯一的地方是在迭代语句之前。

```
label1:
outer-iteration{
	inner-iteration{
		break;//中断内部迭代，回到外部迭代
		
		continue;//使执行点回到内部迭代起始处
		
		continue label1;//同时中断内部迭代和外部迭代，直接转到label1处，实际上继续迭代过程，但是从外部迭代开始。
		
		break label1;中断所有迭代，并回到label1，但不重新进入迭代。完全终止了两个迭代。
	}
}
```

## switch

# 初始化和清理
## 用构造器确保初始化
构造器和类名相同。

不接受任何参数的构造器叫默认构造器。

## 方法重载

### 区分重载方法
每个重载的方法都必须有一个独一无二的参数类型列表。

### 涉及基本类型的重载

### 返回值不能区分重载方法

## 默认构造器
无参构造器，创建一个默认对象。

如果已经定义了一个构造器，编译器就不会自动创建默认构造器。

## this关键字
this关键字只能在方法内部使用，表示对调用方法的那个对象的引用。

### 构造器中调用构造器
### static的含义
static方法就是没有this的方法。

static方法内部不能调用非静态方法，反过来可以，而且可以在没有创建对象的前提下仅仅通过类本身来调用static方法。

## 清理：终结处理和垃圾回收
finalize()一旦垃圾回收器准备好释放对象占用的内存空间，首先调用finalize()方法，并且在下一次垃圾回收动作发生时，才真正回收对象占用内存。

### 垃圾回收器如何工作
引用计数。不能解决循环引用的问题。

任何存活的对象，一定能最终追溯到其存活在堆栈或静态存储区中的引用。从堆栈和静态存储区开始，遍历所有的引用，就能找到所有活的对象。

JIT即时编译器。

## 成员初始化
### 指定初始化
## 构造器初始化
### 初始化顺序
类的内部，变量定义的先后顺序决定了初始化的顺序

### 静态数据的初始化
无论创建多少个对象，静态数据都只占用一份存储区域。static关键字不能用于局部变量。

如果一个域是静态基本类型，也没有初始化，它会获得基本类型的标准初值。如果是一个对象引用，默认初始值是null。

静态初始化只有在必要时刻才进行。只有在第一次对象被创建的时候或者第一次访问静态数据的时候，才会被初始化，此后，静态对象不会再次被初始化。

初始化的顺序是先静态对象，然后是非静态对象。

对象的创建过程：

1. 首次创建类型为Dog的对象时，或者Dog类的静态方法或域被访问时，Java解释器必须查找类路径，以定位Dog.class文件。
2. 然后载入Dog.class，有关静态初始化的所有动作都会执行。因此静态初始化只在Class对象首次加载的时候进行一次。
3. 当用new Dog()创建对象时，首先将在堆上为Dog对象分配足够的内存空间。
4. 这块存储空间将会被清零，这就自动的将Dog对象中所有基本类型数据都设置了默认值。
5. 执行所有出现于字段定义处的初始化动作。
6. 执行构造器。

### 显式的静态初始化
静态块，与其他静态初始化动作一样，静态块仅执行一次，当首次生成这个类的一个对象时，或者首次访问属于这个类的静态数据成员时。

### 非静态实例初始化
实例初始化，用来初始化每一个对象的非静态变量。

## 数组初始化
编译器不允许指定数组的大小。

### 可变参数列表
有了可变参数，再也不用显示的编写数组语法了，指定参数时，编译器实际上会为你去填充数组，获取的仍旧是一个数组。

## 枚举类型
enum。

枚举类型的实例是常量。

# 访问权限控制
从大到小：public，protected，default，private。

## 包：库单元

### 代码组织
### 创建独一无二的包名

## Java访问权限修饰词
### 包访问权限
### public：接口访问权限
### private：你无法访问
### protected：继承访问权限

## 接口和实现
## 类的访问权限
每个编译单元（文件）只能有一个public类。

publci类的名称必须完全与含有该编译单元的文件名相匹配。

类不可以是private的，也不可是protected的。

# 复用类

## 组合语法
只需将对象引用置于新类中即可。

## 继承语法
子类会得到基类中所有的域和方法。

### 初始化基类
当创建了一个导出类的对象时，该对象包含了一个基类的子对象，这个子对象与用基类直接创建的对象是一样的，区别在于基类的子对象被包装在导出类对象内部，而后者来自于外部。

基类子对象初始化，在构造器中调用基类的构造器来执行初始化。

带参数的构造器，如果没有默认的基类构造器，或者想调用一个带参数的基类构造器，就必须使用关键字super显示的编写调用基类构造器的语句。

## 代理

## 结合使用组合和继承

### 确保正确清理

## protected关键字

## 向上转型

## final关键字
### final数据
一个既是static又是final的域，只占据一段不能改变的存储空间。

对于基本类型，final使数值恒定不变。

对于对象引用，final使引用恒定不变。一旦引用被初始化指向一个对象，就无法再把它改为指向另一个对象。对象本身是可以被修改的。

#### 空白final
Java允许生成空白final，是指被声明为final但又未给定初值的域。

必须在域的定义处或者每个构造其中用表达式对final进行赋值。

#### final参数
无法在方法中更改参数引用所指向的对象。这一特性主要用来向匿名内部类传递数据。

### final方法
使用final方法有两个原因，第一是把方法锁定，防止任何继承类修改它的含义。保证在继承中使方法行为保持不变，并且不会被覆盖。

第二个是效率问题，现在已经不使用final优化了。

#### final和private关键字
类中所有的private方法都隐式的指定为是final的。

### final类
当将整个类的整体定义为final时，表明不打算继承该类。

## 初始化及类的加载
类的代码在初次使用时才加载，通常发生在创建类的第一个对象时。

当访问static域或者static方法时也会发生加载。

所有的static对象和static代码段都会在加载时依程序中的顺序而依次初始化。

### 继承与初始化
加载器开始启动找到class文件，加载过程中发现有基类，继续加载基类，以此类推，根基类中的static初始化会被执行，然后是下一个导出类。必要的类都已经加载完，对象就可以被创建了。首先对象中所有的基本类型都会被设为默认值，对象引用被设为null，基类的构造器会被调用。基类构造器和导出类构造器一样，以相同的顺序来经历相同的过程，在基类构造器完成之后，实例变量按次序被初始化，最后构造器其余部分被执行。

# 多态
## 再论向上转型
对象既可以作为它自己本身的类型使用，也可以作为它的基类型使用。这种把某个对象的引用视为对其基类型的引用的做法称为向上转型。

## 转机
### 方法调用绑定
将一个方法调用同一个方法主体关联起来叫做绑定。若程序执行前进行绑定，叫前期绑定。

在运行时根据对象的类型进行绑定，叫后期绑定，也叫动态绑定或者运行时绑定。

Java中除了static方法和final方法之外，其他所有的方法都是后期绑定。

## 构造器和多态
构造器不具有多态性，实际上是static方法，该static声明式隐式的。

### 构造器的调用顺序
基类的构造器总是在导出类的构造过程中被调用，而且是按照继承层次逐渐向上链接，以使每个基类的构造器都能得到调用。

调用构造器的顺序：

1. 调用基类构造器，这个步骤会不断反复递归下去。
2. 按声明顺序调用成员的初始化方法。
3. 调用导出类构造器的主体。

### 继承与清理
### 构造器内部的多态方法的行为

## 协变返回类型
Jdk1.5添加了协变返回类型，表示在导出类中的被覆盖方法可以返回基类方法的返回类型的某种导出类型。

## 用继承进行设计
### 纯继承与扩展
### 向下转型与运行时类型识别

# 接口
## 抽象类和抽象方法
包含抽象方法的类叫做抽象类。如果一个类包含一个或者多个抽象方法，该类必须被限定为抽象的。

## 接口
interface关键字产生一个完全抽象的类，没有提供任何具体实现。接口被用来简历类与类之间的协议。

接口也可以包含域，但是这些域隐式的是static和final的。

接口中被定义的方法必须被定为public。

## 完全解耦
## Java中的多重继承
## 通过继承来扩展接口
## 适配接口
## 接口中的域
接口中任何域都自动是static和final的。

### 初始化接口中的域
域是static的，可在类第一次被加载时初始化，发生在任何域首次被访问时。

## 嵌套接口
接口可以嵌套在类或其他接口中。

## 接口与工厂
接口是实现多重继承的途径，而生成遵循某个接口的对象的典型方式就是工厂方法设计模式。

# 内部类
## 链接到外部类
当生成一个内部类的对象时，此对象与制造它的外围对象之间就有了一种联系，所以它能访问外围对象的所有成员，而不需要任何特殊条件。

内部类还拥有其外围类的所有元素的访问权。

## 使用.this和.new
如果需要生成对外部类对象的引用，使用外部类.this。

如果需要告知某些其他对象，去创建某个内部类的对象，需要在new表达式中提供对其他外部类对象的引用，xxx.new InnerClass()

要想直接创建内部类，必须使用外部类的对象来创建该内部类对象。

如果是静态内部类，不需要对外部类对象的引用。

## 内部类与向上转型
## 在方法和作用域内的内部类
可以在一个方法或者任意的作用域内定义内部类。

## 匿名内部类
参数是final的。

## 嵌套类
如果不想内部类与其外围类对象之间有联系，可以将内部类声明为static，称为嵌套类。

普通内部类对象隐式的保存了一个引用，指向创建它的外围类对象，当内部类是static的，就不是这样了。

1. 要创建嵌套类的对象，不需要其外围类的对象。
2. 不能从嵌套类的对象中访问非静态的外围类对象。

普通内部类的字段与方法只能放在类的外部层次上，所以普通内部类不能有static数据和static字段，也不能包含嵌套类，但是嵌套类可以包含所有这些东西。

### 接口内部的类
正常情况下，不能在接口内部放置任何代码，但嵌套类可以作为接口的一部分。放到接口中的任何类都自动的是public和static的。

### 从多层嵌套类中访问外部类的成员

## 为什么需要内部类
每个内部类都能独立的继承自一个接口的实现，所以无论外围类是否已经继承了某个接口的实现，对于内部类都没有影响。

内部类使得多重继承的解决方案变得完整。

内部类可以有多个实例，每个实例都有自己的状态信息，并且与其外围类对象的信息相互独立。

在单个外围类中可以让多个内部类以不同的方式实现同一个接口，或继承同一个类。

创建内部类对象的时刻并不依赖于外围类对象的创建。

内部类是独立的实体。

## 闭包与回调
闭包是一个可调用的对象，记录了一些信息，这些信息来自于创建它的作用域。

内部类是面向对象的闭包，它不仅包含外围类对象（创建内部类的作用域）的信息，还自动拥有一个指向此外围类对象的引用，在此作用域内，内部类有权操作所有的成员，包括private成员。

### 内部类与控制框架

## 内部类的继承
## 内部类可以被覆盖吗
如果创建了一个内部类，然后继承其外围类并重新定义此内部类时，并不会起什么作用。

## 局部内部类
可以在代码块里创建内部类。

## 内部类标识符
每个类都会产生一个class文件，内部类也会生成，名字是`外围类$内部类：OutClass$InnerClass`。

# 持有对象
## 泛型和类型安全的容器
Java5之前容器主要的问题就是，编译器运行你向容器中插入不正确的类型。

当你指定了某个类型作为泛型参数时，并不仅限于只能将缺钱类型的对象放置到容器中，向上转型也可以像作用域其他类型一样作用域泛型。

## 基本概念
Java容器类库的作用是保存对象。

1. Collection，独立元素序列，这些元素多服从一条或多条规则，List必须按照插入的顺序保存元素，set不能有重复元素，Queue按照排队规则来确定对象产生的顺序。
2. Map，一组成对的键值对对象，允许使用键来查找值。ArrayList允许用数字查找值，它将数字与对象关联在了一起。映射表允许我们使用零一分对象来查找对象，也被成为关联数组，或者字典。

Collection接口概括了序列的概念，一中存放一组对象的方式。

所有的Collection多可以用foreach语法遍历。

## 添加一组记录
Arrays.asList()方法接受一个数组或者是一个用逗号分隔的元素列表（使用可变参数），并将其转换为一个List对象。

Collections.addAll()方法接受一个Collection对象，以及一个数组或逗号分隔的列表，将元素添加到Collection中。

Collection的构造器可以接受另外一个Collection，用来将自身初始化，因此可以使用Arrays.asList来为这个构造器产生输入。

Arrays.asList()输出可以直接使用，将其当做List，但在这种情况下，其底层表示的是数组，因此尺寸不能调整。试图调用add()或者delete()会得到不支持的操作的异常。

## 容器的打印

## List
List将元素维护在特定的序列中。List接口在Collection的基础上添加了大量的方法，使得可以在List的中间插入和移除元素。

* ArrayList，随机访问元素快，在中间插入和删除元素比较慢。
* LinkedList，中间插入和删除快，提供了优化的顺序访问，随机访问比较慢。

## 迭代器
迭代器，是一个对象，工作是遍历并选择序列中的对象。

Java的Iterator只能单向移动，只能用来：

1. 使用方法iterator()要求容器返回一个Iterator，Iterator将准备好返回序列的第一个元素。
2. next()获取序列中下一个元素。
3. hasNext()检查序列中是否还有元素。
4. remove()将迭代器新近返回的元素删除。

### ListIterator
ListIterator是一个更强大的Iterator的子类型，只能用于List类的访问。ListIterator可以双向移动。

可以产生相对于迭代器在列表中指的当前位置的前一个和后一个元素的索引。

可以使用set方法替换访问过的最后一个元素。

通过调用listIterator()方法产生一个指向List开始处的ListIterator。

可以通过调用listIterator(n)来创建一个一开始就指向列表索引为n的元素处的ListIterator。

## LinkedList
LinkedList和ArrayList一样实现了基本的List接口，但是在中间插入和删除比ArrayList更高效，随机访问操作稍微逊色。

LinkedList还添加了可以使其用作栈，队列，双端队列的方法。

getFirst和element方法，返回列表的头，而不移除它。如果List为空，抛NoSuchElementException。peek方法会在列表为空时返回null。

removeFirst和remove移除并返回列表的头。如果List为空，抛NoSuchElementException。poll方法会在列表为空时返回null。

addFirst和add，addLast将某个元素插入到列表的尾部。

removeLast移除并返回列表的最后一个元素。

## Stack
栈，通常指后进先出LIFO的容器。

LinkedList具有能够实现栈的所有功能的方法，可以直接将LinkedList作为栈使用。

## Set
Set不保存重复元素。HashSet专门针对快速查找进行了优化。

Set具有与Collection完全一样接口。没有任何额外的功能，实际上Set就是Collection，只是行为不同。

Set是基于对象的值，来确定归属性的。

TreeSet将元素存储在红黑树数据结构中，HashSet使用散列函数，LinkedSet也使用了散列。

## Map
可以返回它的键的Set和值的Collection。或者键值对的Set。

## Queue
队列是先进先出FIFO的容器。

LinkedList提供了方法以支持队列的行为，并且实现了Queue接口，因此LinkedList可以作为Queue的一种实现。

offer方法将元素插入到队尾。

peek和element在不移除的情况下返回队头。队列为空，peek返回null，element抛异常。

poll和remove移除并返回队头，队列为空poll返回null，remove抛异常。

### PriorityQueue
优先级队列，声明下一个弹出元素是最需要的元素，具有高优先级。

在PriorityQueue上调用offer方法插入对象时，这个对象会在队列中被排序，默认使用自然顺序，还可以通过自己的Comparator来修改顺序。

PriorityQueue可保证调用peek(),poll(),remove()方法时，获取的元素时队列中优先级最高的元素。

## Collection和Iterator
Collection是描述所有序列容器的共性的根接口。AbstractCollection类提供了Collection的默认实现。

## Foreach与迭代器
foreach语法主要用于数组，也可以应用于任何Collection对象。

Jdk1.5引入了新接口Iterable，包含一个能够产生Iterator的iterator()方法，并且Iterable接口被foreach用来在序列中移动，任何实现了Iterable的类，都可以将它用于foreach语句中。

## 通过异常处理错误
使用new在堆上创建异常对象。

### 异常参数
与使用Java中其他对象一样，用new在堆上创建异常对象，伴随着存储空间的分配和构造器的使用，所有标准异常都有两个构造器，一个是默认的，一个是接受字符串作为参数。

## 捕获异常
### try块
### 异常处理程序

## 创建自定义异常

## 异常说明
throws

### 异常链
捕获一个异常后抛出另一个异常，并且希望把原始异常信息保存下来，这称为异常链。

Throwable的子类在构造器中可以接受一个cause对象作为参数，cause表示原始异常。

## Java标准异常
Throwable表示任何可被作为异常抛出的类。Throwable对象可分为两种类型，Error表示编译时和系统错误，Exception可被抛出的基本类型。

## 使用finally进行清理
无论try中是否抛异常，finally中都会执行。

### finally用来做什么
清理资源。

### 在return中使用finally
finally子句总会执行，所以在一个方法中可以从多个点返回。

## 异常的限制
在覆盖方法的时候，只能抛出在基类方法的异常说明里列出的异常。

## 构造器
## 异常匹配

# 字符串
## 不可变String
String对象是不可变的。每一个看起来会修改String值的方法，实际上是创建了一个全新的String对象，以包含修改后的字符串内容，最初的String对象未改变。

每次把String对象作为方法的参数时，都会复制一份引用。

## 重载"+"与StringBuilder
String对象是不可变的。

StringBuilder是Jdk1.5引入的，之前是StringBuffer线程安全的。

## 无意识的递归

## String上的操作
当需要改变字符串的内容时，String类的方法都会返回一个新的String对象。如果内容没有发生变化，String的方法只是返回指向原对象的引用。

## 格式化输出
### printf()
### System.out.format()
### Formatter类
### 格式化说明符
%[argument_index$][flags][width][.precision]consoversion

### Formatter转换

### String.format()

## 正则表达式
### 基础
一个负号在最前面`-?`

`\d`表示数字

可能有一个负号，后面跟着一位或者多位数字：`-?\\d+`

String自带了split()方法，将字符串从正则表达式匹配的地方切开。

### 创建正则表达式
。。。

## 扫描输入
Scanner的构造器可以接受任何类型的输入对象，包括File对象，InputStream，String，Readable对象。

### Scanner定界符
Scanner根据空白字符对输入进行分词。还可以使用正则表带是来指定自己的所需的定界符。

## StringTokenizer
可用来分词。基本已经废弃了。

# 类型信息
运行时识别对象和类的信息，主要有两种方式，一种是传统的RTTI，它假定我们在编译时已经知道了所有的类型。另一种是反射机制，允许我们在运行时发现和使用类的信息。

## Class对象
Class对象包含了与类有关的信息。

类加载器子系统实际上可以包含一条类加载器，但是只有一个原生类加载器。

所有的类都是在对其第一次使用时，动态加载到JVM中的。当程序创建第一个对类的静态成员引用时，就会加载这个类。

类加载器首先检查这个类的Class对象是否已经加载，如果尚未加载，默认的类加载器就会根据类名查找class文件。在这个类的字节码被加载时，他们会接受验证，以确保其没有被破坏，并且不包含不良Java代码。

### 类字面量
为了使用类而做的准备工作实际包含三个步骤：

1. 加载，由类加载器执行，查找字节码，并从字节码中创建一个Class对象。
2. 链接，验证类中的字节码，为静态域分配存储空间，解析这个类创建的对其他类的所有引用。
3. 初始化，如果该类具有超类，则对其初始化，执行静态初始化器和静态初始化块。

### 泛化的Class引用
Class引用总是指向某个Class对象，他可以制造类的实例，包含可作用域这些实例的所有方法代码，包含该类的静态成员。

## 反射：运行时的类信息
Class类与java.lang.reflect类库一起对反射的概念进行了支持，该类库包含了Field，Method以及Constructor类。

这些类型的对象是由JVM在运行时创建的，用于表示未知类里对应的成员。这样就可用Constructor创建新的对象，用get和set方法读取和修改与Field对象关联的字段。用invoke方法调用与Method对象关联的方法。

## 动态代理
Java动态代理，可以动态的创建代理并动态的处理对所代理方法的调用。

调用Proxy.newProxyInstance()可以创建动态代理，这个方法需要得到一个类加载器，一个你希望该代理实现的接口列表，以及InvocationHandler接口的一个实现。动态代理可以将所有调用重定向到调用处理器。

## 空对象
## 接口与类型信息

# 泛型
final类不能被扩展，其他任何类都可以被扩展。

## 泛型接口
## 泛型方法
## 匿名内部类
## 擦除的神秘之处
Java泛型是使用擦除来实现的，当你使用泛型时，任何具体的类型信息都被擦除了。

不能创建泛型数组。

## 边界
extends

## 通配符

## 问题
任何基本类型都不能作为类型参数。

# 数组
## 数组为什么特殊
Java中数组是一种效率最高的存储和随机访问对象引用序列的方式。数组是一个简单的线性序列，使得元素访问非常快速。

数组大小被固定，生命周期中不可变。

## 数组是第一级对象
无论使用哪种类型的数组，数组标识符其实只是一个引用，指向在堆中创建的一个真实对象。

## 返回一个数组

## 多维数组
## 数组与泛型
不能实例化具有参数化类型的数组。

## Arrays实用功能
equals()比较两个数组是否相等，deepEquals()用于多维数组。

fill()填充数组。

sort()对数组排序。

binarySerach()在已经排序的数组中查找元素。

### 复制数组
System.arraycopy();

如果复制对象数组，那么只是复制了对象的引用，浅拷贝。

### 数组的比较
equals()元素个数相等，对应位置的元素也相等。

# 容器的深入研究
Jdk1.5新添加了：

* Queue接口，实现PriorityQueue和各种BlockingQueue。
* ConcurrentMap接口及实现ConcurrentHashMap，用于多线程机制的。
* CopyOnWriteArrayList和CopyOnWriteArraySet，用于多线程机制。
* EnumSet和EnumMap。
* Collections的多个便利方法。

## 填充容器
## Collection的功能方法
Collection中所有的操作也是Set和List中的所有操作，List还有额外功能。Map不是继承自Collection。

## List的功能方法
## Set和存储顺序
Set接口，存入Set的每个元素必须是唯一的，Set不保存重复元素。加入Set的元素必须定义equals方法以确保对象的唯一性。Set与Collection有完全一样的接口，Set接口不保证维护元素的次序。

HashSet为快速查找而设计的Set，存入HashSet的元素必须定义hashCode()。

TreeSet保持次序的Set，底层为树结构，元素必须实现Comparable接口。

LinkedHashSet具有HashSet的查询速度，且内部使用链表维护元素的顺序。元素必须定义hashCode()方法。

### SortedSet
SortedSet的元素可以保证处于排序状态。

## 队列
Queue在Jdk1.5中仅有的两个实现是LinkedList和PriorityQueue。差异在于排序行为而不是性能。

### 优先级队列
PriorityQueue。

### 双向队列
Deque。

## 理解Map
HashMap，TreeMap，LinkedHashMap，WeakHashMap，ConcurrentHashMap，IdentityHashMap。

### 性能
HashMap使用了特殊的值，称作散列码，来取代对键的缓慢搜索。HashMap使用对象的hashCode进行快速查询。

HashMap基于散列表的实现，取代了HashTable，插入和查询键值对的开销是固定的，可以通过构造器设置容量和负载因子，以调整容器的性能。

LinkedHashMap类似于HashMap，但是迭代遍历时，取得键值对的顺序是插入次序，只比HashMap慢一点，迭代访问时更快，它使用链表维护内部次序。

TreeMap基于红黑树的实现，结果都是经过排序的。

WeakHashMap弱键映射，允许释放映射所指向的对象。

ConcurrentHashMap一种线程安全的Map，不涉及同步加锁。

IdentityHashMap使用==代替equals()对键进行比较的散列映射。

任何键都必须有一个equals()方法，如果键被用于散列Map，那么还必须有恰当的hashCode方法。如果被用于TreeMap，必须实现Comparable。

### SortedMap
可以确保键处于排序状态。

### LinkedHashMap
散列化所有元素，在遍历时，又以元素的插入顺序返回键值对。

## 散列与散列码
使用自己的类作为HashMap的键，必须同时重载hashCode和equals方法。

### 理解hashCode()
### 为速度而散列
散列使得查询得以快速进行。

查询一个值的过程是：首先计算散列码，然后使用散列码查询数组。如果能够保证没有冲突，就有了一个完美的散列函数。通常冲突由外部链接处理，数组并不直接保存值，而是保存值的list，然后对list中的值使用equals方法进行线性查询。

### 覆盖hashCode()
无论何时，对同一个对象调用hashCode都应该生成同样的值。

String有个特点：如果程序中有多个String对象，都包含相同的字符串序列，那么这些String对象都映射到同一块内存区域。

## 实用方法
java.util.Collections类的静态方法。

## 持有引用
java.lang.ref类库包含了一组类，为垃圾回收提供了更大的灵活性。

SoftReference，WeakReference，PhantomReference。

SoftReference可用以实现敏感的高速缓存。

WeakReference不妨碍垃圾回收器回收映射的键或值。

Phantomreference用于调度回收前的清理工作。

### WeakHashMap

## Java1.0/1.1的容器
### Vector和Enumeration
Vector与ArrayList类似，Enumeration迭代。

### HashTable
HashTable与HashMap类似

### Stack
继承自Vector

### BitSet

# Java I/O系统
## File类
既能代表文件的名称，也能代表一个目录下一组文件的名称。如果它指的是一个文件集，我们就可以对此集合调用list方法，会返回一个字符数组。

### 目录列表器
查看目录列表，可以使用两种方法来使用File对象。调用不带参数的list()方法，可以获得此File对象包含的全部列表。如果想要获得受限列表，要用到目录过滤器。

### 目录实用工具
### 目录的检查及创建
可以用File对象来创建新的目录或尚不存在的整个目录路径。还可以查看文件的特性，检查某个File对象代表的是一个文件还是目录，可以删除文件。

## 输入和输出
流，代表任何有能力产出数据的数据源对象或者有能力接收数据的接收端对象。

Java的I/O分为输入和输出两部分。

任何继承自InputStream和Reader的类都含有read()方法，用于读取单个字节或者字节数组。

任何继承自OutputStream和Writer的类都包含有write()方法，用于写单个字节或者字节数组。

### InputStream类型
ByteArrayInputStream允许将内存的缓冲区当做InputStream使用。

StringBufferInputStream将String转换成InputStream。

FileInputStream从文件中读取信息。

PipedInputStream产生用于写入相关的PipedOutputStream的数据，实现管道化概念。

SequenceInputStream将两个或多个InputStream对象转换成单一的InputStream。

FilterInputStream抽象类，作为装饰器的接口。为其他InputStream类提供有用功能。

### OutputStream类型
ByteArrayOutputStream在内存中创建缓冲区，所有送往流的数据都要放置在此缓冲区。

FileOutputStream用于将信息写至文件。

PipedOutputStream任何写入其中的信息都会自动作为相关PipedInputStream的输出，实现管道化概念。

FilterOutputStream抽象类，作为装饰器接口。

## 添加属性和有用接口
### 通过FilterInputStream从InputStream读取数据

* DataInputStream
* BufferedInputStream
* LineNumberInputStream
* PushbackInputStream

### 通过FilterOutputStream向OutputStream写入

* DataOutputStream
* PrintStream
* BufferedOutputStream

## Reader和Writer
提供了兼容Unicode与面向字符的I/O功能。

InputStreamReader可以把InputStream转换为Reader。

OutputStreamWriter可以把OutputStream转换为Writer。

## 自我独立的类：RandomAccessFile
适用于由大小已知的记录组成的文件，可以使用seek()将记录从一处转移到另一处，然后读取和修改记录。

getFilePointer()用于查找当前所处的文件位置。seek()用于在文件内移至新的位置。length()判断文件的最大尺寸。

RandomAccessFile的大多数功能由nio存储映射文件所取代。

## I/O流的典型使用方式
### 缓冲输入文件
如果想要打开一个文件用于字符输入，可以使用以String或File对象作为文件名的FileInputReader，为提高速度，希望对文件进行缓冲，可以将所产生的引用传给BufferedReader。

### 读写随机访问文件
使用RandomAccessFile。

## 标准I/O
System.in，System.out，System.err。

## 新N/O
jdk1.4的java.nio.*包中引入了新的类库。

速度的提高来自于所使用的结构更接近于系统执行I/O的方式，通道和缓冲器。

与通道交互的缓冲器是ByteBuffer。

将字节存放于ByteBuffer的方法之一是使用“put”方法直接进行填充。也可以使用wrap()方法将已存在的字节数组包装到ByteBuffer中。

allocate(),allocateDirect()

ByteBuffer只能保存字节类型的数据。

### 视图缓冲器

### 用缓冲器操纵数据
想把一个字节数组写到文件中去，应该使用ByteBuffer.wrap()方法把字节数组包装起来，然后用getChannel()方法在FileOutputStream上打开一个通道，接着将来自ByteBuffer的数据写到FileChannel中。

### 缓冲器的细节
Buffer由四个索引组成：mark标记，position位置，limit界限，capacity容量。

### 内存映射文件
内存映射文件允许我们创建和修改那些因为太大而不能放入内存的文件。

### 文件加锁
Java的文件加锁直接映射到本地操作系统的加锁工具。

通过FileChannel调用tryLock或者lock方法，就可以获得整个文件的FileLock。

也可以对文件的一部分进行加锁。

对独占锁或者共享锁的支持必须由底层的操作系统提供。锁的类型可以通过FileLock.isShared()进行查询。

## 压缩

## 对象序列化
Java对象序列化将那些实现了Serializable接口的对象转换成一个字节序列，并能够在以后将这个字节序列完全恢复为原来的对象。

对象序列化主要为了支持两种特性，一是Java的远程方法调用RMI，二是对JavaBeans来说对象的序列化是必须的。

要序列化一个对象，首先要创建某些OutputStream，然后将其封装在ObjectOutputStream对象内，这时只需要调用writeObject()即可将对象序列化。

### 序列化的控制
Externalizable对序列化过程进行控制。

#### transient关键字
将字段关闭序列化。

## XML
## Preferences
读取用户的偏好以及程序配置项的设置。

# 枚举类型
## 基本enum特性
调用enum的values方法可以遍历enum实例、values方法返回enum实例的数组，该数组中的元素严格保持其在enum中声明的顺序。

# 注解
注解，也称为元数据，为我们在代码中添加信息提供了一种形式化的方法，使我们可以在稍后某个时刻非常方便的使用这些数据。

# 并发
## 基本的线程机制
### 定义任务
描述任务，可以由Runnable接口来提供。定义任务，只需要实现Runnable接口并编写run方法。

Thread.yield()的调用是对线程调度器的一种建议，我已经执行完声明周期中红最重要的部分了，此刻正是切换给其他任务执行一段时间的大好时机。

从Runnable导出一个类时，它必须有run()方法但是这个方法不会产生任何内在的线程能力，要实现线程行为，需要显式的将一个任务附着到线程上。

### Thread类
将Runnable对象转变为工作任务，是把他提交给一个Thread构造器。

调用Thread对象的start()方法为该线程执行必须的初始化操作，然后调用Runnable的run方法，以便在这个新线程中启动该任务。

### 使用Executor
Executor可以管理Thread对象。

### 从任务中产生返回值
Runnable是执行工作的独立任务，但它不返回任何值。

Callable可以有返回值，是从call()方法中返回的值，必须使用ExecutorService.submit()方法调用。

submit()方法产生Future对象，可以使用isDone查询Future是否已经完成。任务完成时，具有一个结果，get()来获取结果。

get()会阻塞，直至结果准备就绪，

### 休眠
sleep()将使任务中止执行给定的时间。

对sleep()的调用可以抛出InterruptedException异常。

### 优先级
getPriority和setPriority

### 让步
yield()

### 后台线程
必须在线程启动之前调用serDaemon()方法，才能把它设置为后台线程。

### 加入一个线程
一个线程可以在其他线程之上调用join()方法。如果某个线程在另一个线程t上调用join方法，此线程会被挂起，直到目标线程t结束才能恢复。

也可以在调用join时，带上一个超时参数。

join方法可以被中断，在调用线程上调用interrupt()方法。

### 线程组
没啥用

### 捕获异常

## 共享受限资源
### 解决共享资源竞争
采用序列化访问共享资源的方案。给定时刻只允许一个任务访问共享资源。通常在代码前面加上一条锁语句来实现，使得一段时间内只有一个任务可以运行这段代码，锁语句产生了一种互相排斥的效果，所以常称为互斥量。

synchronized

#### 使用显式的Lock对象
Lock对象必须被显式的创建锁定和释放。

### 原子性与易变性
原子性可以应用于除long和double之外的所有基本类型之上的简单操作，对于读取和写入的操作，可以保证他们会被当做不可分的操作来操作内存。

long和double使用volatile关键字就会获得原子性。

### 原子类
AtomicInteger，AtomicLong，AtomicReference

### 临界区
synchronized，同步控制块。

### 线程本地存储
线程本地存储是一种自动化机制，可以为使用相同变量的每个不同的线程都创建不同的存储。

ThreadLocal。

ThreadLocal对象通常当做静态域存储，创建时，只能通过get和set方法来访问该对象的内容。get方法将返回与其线程相关联的对象的副本，set会将参数插入到为其线程存储的对象中，并返回存储中原有的对象。

## 终结任务
### 在阻塞时终结
#### 线程状态
线程可以处于四种状态之一：

1. 新建new，线程被创建时，它只会短暂的处于这种状态。此时它已经分配了必须的系统资源，并执行了初始化，此刻线程已经有资格或者CPU时间了，之后调度器将把这个线程转变为可运行状态活或阻塞状态。
2. 就绪Runnable，这种状态下只要调度器把时间片分给线程，线程就可以运行。
3. 阻塞Blocked，线程能运行，但有某个条件阻止它的运行。
4. 死亡Dead。

#### 进入阻塞状态

1. 通过调用sleep方法使任务进入休眠状态，任务在指定的时间内不会运行。
2. 通过调用wait使线程挂起。直到得到了notify或notifyAll消息（Jdk1.5并发库使用signal或signalAll方法），线程才会进入就绪状态。
3. 任务在等待某个输入或输出完成。
4. 任务试图在某个对象上调用其同步方法，但是对象锁不可用。

### 中断
Thread类包含interrupt方法，可以终止被阻塞的任务，这个方法将设置线程的中断状态。如果一个线程已被阻塞，或者试图执行一个阻塞操作，那么设置这个线程的中断状态将抛出InterruptedException。当抛出异常或者该任务调用Thread.interrupted()时，中断状态将被复位。

Executor上调用shutdownNow()，将发送一个interrupt调用给他启动的所有线程。

cancel()是一种中断由Executor启动的单个线程的方式。

### 检查中断
当你在线程上调用interrupt时，中断发生的唯一时刻是在任务要进入到阻塞操作中，或者已经在阻塞操作内部时。

## 线程之间的协作
### wait()与notifyAll()
wait可以等待某个条件发生变化，而改变这个条件超出了当前方法的控制能力。通常这种条件将由另一个任务来改变。

wait会在等待外部世界产生变化的时候，将任务挂起，并且只有在notify或notifyAll发生时，即表示发生了某些感兴趣的事，这个任务才会被唤醒并去检查所产生的变化。

调用sleep的时候没有释放锁。

当任务在方法里遇到对wait的调用时，线程的执行被挂起，对象上的锁被释放。

1. 在wait期间对象锁时释放的。
2. 可以通过notify，notifyAll或者时间到期，从wait中恢复执行。

wait，notify，notifyAll是基类Object的一部分，不是Thread的一部分。

只能在同步方法或者同步块里调用wait，notify，notifyAll。

因为不用操作锁，所以sleep可以在非同步控制方法里调用。

### 生产者与消费者
#### 使用显式的Lock和Condition对象
可以通过在Condition上调用await()来挂起一个任务。当外部条件发生变化，意味着某个任务应该继续执行时，你可以通过调用signal()来通知这个任务，从而唤醒一个任务，或者调用signalAll()来唤醒所有在这个Condition上被其自身挂起的任务。

### 生产者-消费者与队列
可以使用同步队列来解决任务协作问题，同步队列任何时候都只允许一个任务插入或移除元素。

java.util.concurrent.BlockingQueue接口中提供了这个队列。

LinkedBlockingQueue，无界队列。

ArrayBlockingQueue，具有固定尺寸，可以在它被阻塞之前，向其中放置有限数量的元素。

如果消费者试图从队列中获取对象，而该队列为空，这些队列还可以挂起消费者任务，并且当有更多的元素可用时恢复消费者任务。

### 任务间使用管道进行输入/输出
PipedWriter类和PipedReader类。管道基本上是一个阻塞队列。

## 死锁
当以下四个条件同时满足时，就会发生死锁：

1. 互斥条件。任务使用的资源中至少有一个是不能共享的。
2. 至少有一个任务它必须持有一个资源且正在等待获取一个当前被别的任务持有的资源。
3. 资源不能被任务抢占，任务必须把资源释放当做普通事件。
4. 必须有虚幻等待，一个任务等待其他任务所持有的资源，后者又等待另一个任务所持有的资源。

要防止死锁，破坏其中一个即可。

## 新类库中的构件
### CountDownLatch
被用来同步一个或多个任务，强制他们等待由其他任务执行的一组操作完成。

可以向CountDownLatch对象设置一个初始计数值，任何在这个对象伤调用await的方法都将阻塞，直至这个计数为0。其他任务结束工作时，可以在该对象上调用countDown()来减少这个计数值。CountDownLatch只触发一次。

调用countDown的任务在产生这个调用时，并没有被阻塞，只有对await的调用才会被阻塞，直至计数值到达0。

CountDownLatch的典型用法是将一个程序分为n个相互独立的可解决任务，并创建值为0的CountDownLatch。每个任务完成时，都会在锁存器上调用countDown，等待问题被解决的任务在这个锁存器上调用await，将他们自己拦住，直至锁存器计数结束。

### CyclicBarrier
适用于：你希望创建一组任务，他们并行的执行工作，然后在进行下一步骤之前等待，直到所有任务都完成。使得所有的并行任务都将在栅栏处队列。很像CountDownLatch，但是CountDownLatch只触发一次，CyclicBarrier可以多次重用。

### DelayQueue
这是一个无界的BlockingQueue，用于放置实现了Delayed接口的对象，其中的对象只能在其到期时才能从队列中取走，这种队列是有序的，即队头对象延迟到期的时间最长。

Delayed接口有一个方法名为getDelay()可以告知延迟到期有多长时间，或者延迟在多长时间之前已经到期。

### PriorityBlockQueue
优先级队列，具有可阻塞的读取操作。

### 使用ScheduledExecutor
ScheduledThreadPoolExecutor将对象设置为在将来的某个时刻执行。schedule()运行一次任务。scheduleAtFixedRate()每隔归档的时间重复执行任务。

### Semaphore
正常的锁在任何时刻都只允许一个任务访问一项资源，而计数信号量允许n个任务同时访问这个资源，你还可以将信号量看作是在向外分发使用资源的许可证。

### Exchanger
是两个任务之间交换对象的栅栏。这些任务进入栅栏时，他们各自有用一个对象，当他们离开时，都拥有之前由对象持有的对象。

### 免锁容器
对容器的修改可以与读取操作同时发生。修改是在容器数据结构的某个部分的一个单独的副本上执行的。

CopyOnWriteArrayList写入将导致创建整个底层数组的副本，而源数组将保留在原地，使得复制的数组在修改时，读操作可以安全的执行，修改完成之后，一个原子性的操作将把新的数组换入，使新的读取操作可以看到这个新的修改。

CopyOnWriteArrayList当多个迭代器同时遍历和修改这个列表时，不会抛出ConcurrentModificationException。

CopyOnWriteArraySet使用CopyOnWriteArrayList来实现其免锁行为。

ConcurrentHashMap和ConcurrentLinkedQueue使用了类似的技术，允许并发的读取和写入，但是容器中只有部分内容而不是整个容器可以被复制和修改。然而在任何修改完成之前，读取者仍旧不能看到他们。

### 乐观加锁
CAS

### ReadWriteLock
对向数据结构相对不频繁的写入，但是有多个任务要经常读取这个数据结构的这类情况作了优化。ReadWriteLock使得你可以同时有多个读者，只要他们都不试图写入即可。如果写锁已被其他任务持有，所有读取都不能访问。

## 活动对象
Future，可以使用它来发现何时任务完成，并收集实际的返回值。
