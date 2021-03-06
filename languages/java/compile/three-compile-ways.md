### Java三种编译方式
#### 前端编译
Java源码文件（.java）编译成Class文件(.class)的过程
即把满足Java语言规范的程序转化为满足JVM规范所要求格式的功能

##### 优点:
- 这阶段的优化是指程序编码方面的
- 许多Java语法新特性（"语法糖": 泛型、内部类等等）, 是靠前端编译器实现的, 而不是依赖虚拟机
- 编译成的Class文件可以直接给JVM解释器解释执行, 省去编译时间, 加快启动速度

##### 缺点:
- 对代码运行效率几乎没有任何优化措施
- 解释执行效率较低, 所以需要结合下面的JIT编译
- Oracle javac、Eclipse JDT中的增量式编译器（ECJ）

#### 后端编译/即时(JIT)编译
通过Java虚拟机（JVM）内置的即时编译器（Just In Time Compiler，JIT编译器）
在运行时把Class文件字节码编译成本地机器码的过程

##### 优点:
- 通过在运行时收集监控信息, 把 "热点代码"（Hot Spot Code）编译成与本地平台相关的机器码, 并进行各种层次的优化
- 可以大大提高执行效率

##### 缺点:
- 收集监控信息影响程序运行
- 编译过程占用程序运行时间（如使得启动速度变慢）
- 编译机器码占用内存

JIT编译速度及编译结果的优劣，是衡量一个JVM性能的很重要指标

#### 静态提前编译（Ahead Of Time, AOT编译）
##### 优点:
- 编译不占用运行时间, 可以做一些较耗时的优化, 并可加快程序启动
- 把编译的本地机器码保存磁盘, 不占用内存，并可多次使用

##### 缺点:
- Java语言的动态性（如反射）带来了额外的复杂性, 影响了静态编译代码的质量
- 一般静态编译不如JIT编译的质量, 这种方式用得比较少

#### 前端编译 + JIT编译
程序运行前，直接把Java源码文件（.java）编译成本地机器码的过程
- 首先通过前端编译把符合Java语言规范的程序代码转化为满足JVM规范所要求Class格式
- 然后程序启动时Class格式文件发挥作用, 解释执行, 省去编译时间, 加快启动速度
- 针对Class解释执行效率低的问题, 在运行中收集性能监控信息, 得知 "热点代码"
- JIT逐渐发挥作用, 把越来越多的热点代码 "编译优化成本地代码, 提高执行效率
