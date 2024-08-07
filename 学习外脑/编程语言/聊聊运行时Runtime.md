#编程语言 #永久 

|          | 编译期                         | 运行时                          |
|------------------|--------------------------------|---------------------------------|
| **发生时间**      | 发生在构建过程中，源代码被翻译为目标代码或中间代码。 | 发生在程序实际运行时，加载到内存并执行。  |
| **可能出现的错误** | - 静态检查错误，如语法错误、类型错误等。   | - 动态运行时错误，如空指针引用、除零错误等。   |
| **排查难度**      | - 错误信息清晰，易于定位和修复。         | - 错误可能更难以排查，需要使用调试工具进行追踪。   |

|  | 无运行时 | 有运行时 |
| :--: | ---- | ---- |
| **内存管理** | 程序员需要手动管理内存分配和释放。 | 运行时环境负责内存管理，可能包括自动内存分配和垃圾回收。 |
| **线程模型** | 通常依赖操作系统提供的线程机制。 | 可能提供自己的线程管理机制，与操作系统的线程模型有一定差异。 |
| **系统调用** | 直接使用操作系统提供的系统调用接口。 | 通过运行时环境提供的接口进行系统调用，可能会屏蔽一些底层细节。 |
| **运行效率** | 对于底层硬件和操作系统有更直接的控制。 | 需要运行时环境的支持，可能引入一些开销。 |
