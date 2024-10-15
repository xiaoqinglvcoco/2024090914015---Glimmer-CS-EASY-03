# 2024090914015---Glimmer-CS-EASY-03
微光招新题cs3
## C语言内存模型
### 一些内存分区
| 内存分区    | 具体含义 |
| ----------- | ----------- |
| 程序代码区 (code)| ==1.具体含义：== 程序代码区通常指的是在程序编译后，存放二进制代码的区域。这个区域由操作系统进行管理。源代码是由一系列的指令、函数、变量和其他语言元素组成，用于实现特定的功能或解决特定的问题。在程序执行时，这些指令被加载到程序代码区，并由CPU逐条执行。  ==2.应用场景：== 程序代码区是程序的核心部分，它包含了实现程序功能所需的所有指令。操作系统、应用程序，游戏，都需要通过程序代码区中的指令来执行各种操作。     ==3. 调用方式：== 程序代码区的指令通常由CPU逐条执行。在程序启动时，程序代码区会被加载到内存中，然后CPU按照指令的顺序逐条执行。程序员通过编写源代码来定义这些指令，并通过编译器将其转换为机器代码以供CPU执行。|
| 常量区 (constant)| ==1.具体含义：== 常量区用于存储程序中定义的常量值。常量是程序中固定不变的值，它们在定义后不能被修改。在编程语言中，常量是与值的绑定关系不可改变的标识符，必须在定义时（或在编译时）赋值，且一旦赋值后，就不能再被重新赋予新的值。常量区确保了这些值在程序运行期间保持不变。   ==2.应用场景：== 常量区通常用于存储程序中不需要改变的值，如配置参数、数学常数、枚举值等。这些值在程序运行期间保持不变，有助于程序的稳定性和可读性。   ==3.调用方式：== 在程序中，常量通过常量名进行引用。由于常量值在编译时就已经确定，因此它们的访问速度通常比变量更快。|
|全局数据区 (global data)|  ==1.具体含义：== 全局数据区用于存储全局变量和静态变量。全局变量是在整个程序范围内都可以访问的变量，而静态变量则具有静态存储期，即在程序执行期间它们的值保持不变（尽管它们可以存储可变的数据）。全局数据区确保了这些变量在程序运行期间始终存在，并且可以在程序的任何部分被访问。    ==2.应用场景：== 全局数据区常用于存储需要在多个函数或模块之间共享的数据。由于全局变量在程序的整个运行期间都存在，因此它们可以用于存储一些需要在整个程序生命周期内保持不变的数据。     ==3.调用方式：== 程序员在编写源代码时，可以使用特定的语法（如C语言中的global关键字或直接在函数外部定义变量）来定义全局变量。在编译时，这些全局变量会被分配到全局数据区中。在程序运行时，程序员可以通过变量名来访问和修改这些全局变量的值。|
|堆区 (heap)| ==1.具体含义：== 堆区是程序运行时用于动态分配内存的区域。与全局数据区和栈区不同，堆区允许程序在运行时根据需要分配和释放内存，这也要求程序员必须小心管理内存，以避免内存泄漏和碎片化等问题。  ==2.应用场景：== 堆区常用于存储一些在程序运行期间才需要分配内存的数据结构，如链表、树、图等。由于堆区允许程序在运行时根据需要动态地分配和释放内存，因此它提供了更大的灵活性和动态性。   ==3.调用方式：== 堆区的内存分配是由程序员手动控制的，程序员在编写源代码时，可以使用特定的函数（如C语言中的malloc、calloc、realloc和free函数）来在堆区中分配和释放内存。在程序运行时，这些函数会根据需要向操作系统请求内存，并将其分配给堆区中的变量。程序员需要负责在适当的时候释放这些内存，以避免内存泄漏。|
|动态链接库| ==1.具体含义：== 动态链接库（Dynamic Link Library，DLL）是微软公司在Windows操作系统中实现共享函数库概念的一种实作方式。它允许程序在运行时动态地加载和链接到所需的库文件，从而实现了代码的重用和模块化。动态链接库使得程序可以更加灵活地更新和扩展功能，而无需重新编译整个程序。    ==2.应用场景：== 动态链接库常用于实现代码的共享和重用。通过将常用的功能封装在动态链接库中，程序员可以在多个程序之间共享这些功能，从而提高开发效率和代码质量。此外，动态链接库还允许程序在运行时动态地加载和卸载库文件，从而实现了更灵活的模块化和更新机制。    ==3.调用方式：== 程序员在编写源代码时，可以使用特定的语法（如C语言中的#include指令和__declspec(dllimport)、__declspec(dllexport)关键字）来引用和导出动态链接库中的函数和数据。在编译时，编译器会将这些引用和导出信息嵌入到生成的可执行文件中。在程序运行时，操作系统会根据需要加载和链接动态链接库文件，并提供对其中函数的访问。|
|栈区 (stack)| ==1.具体含义：== 栈区是程序用于存储局部变量和函数调用信息的内存区域。栈是一种后进先出（LIFO）的数据结构，它允许程序在函数调用时自动地分配和释放内存。栈区确保了函数调用的正确性和局部变量的生命周期管理。当函数被调用时，它的参数、局部变量和返回地址等信息会被压入栈中；当函数返回时，这些信息会从栈中弹出，并释放相应的内存空间。   ==2.应用场景：== 栈区常用于存储函数调用过程中的临时数据和返回地址等信息。由于栈区具有后进先出的特性，因此它非常适合用于实现函数调用和递归等算法。    ==3.调用方式：== 程序员在编写源代码时，无需显式地管理栈区的内存分配和释放。当函数被调用时，操作系统会自动在栈区中分配内存来存储该函数的局部变量和返回地址等信息。当函数返回时，操作系统会自动释放这些内存空间。程序员只需要在编写函数时正确地使用局部变量和返回语句即可|
### 导学问题
1. 什么是“栈溢出”？
是一种常见的编程错误，指的是当程序在栈（stack）中分配的数据超过其容量限制时发生的现象。具体来说，栈是一种先进后出（LIFO）的数据结构，用于存储局部变量和函数调用时的信息（如返回地址、参数等）。当栈上的数据量超出其预分配的空间时，就会发生栈溢出。这种情况可能导致程序崩溃或安全漏洞，如缓冲区溢出攻击。
2. 堆区和栈区的区别是什么？
    1. 内存分配与释放方式
    堆区：
    分配方式：堆区的内存分配是由程序员手动控制的（或在某些高级语言中由垃圾回收器自动管理）。程序员可以使用特定的内存分配函数或运算符（如C++中的new、malloc等）来在堆上动态分配内存。
    释放方式：同样地，程序员也需要手动释放堆区已分配的内存（或使用垃圾回收机制）。这通常通过调用相应的内存释放函数或运算符（如C++中的delete、free等）来实现。
    栈区：
    分配方式：栈区的内存分配是由编译器和运行时系统自动管理的。当函数被调用时，系统会在栈上为函数的局部变量、参数等分配内存空间。
    释放方式：栈区的内存释放也是自动的。当函数执行完毕并返回时，系统会自动回收栈上为该函数分配的内存空间。
    **（即堆区手动，栈区自动）**
    2. 内存空间大小与扩展方向
    堆区：
    空间大小：堆区的大小受限于计算机系统中有效的虚拟内存。因此，堆区可以获得较大的内存空间，用于存储大型数据结构或对象。
    扩展方向：堆区是向高地址扩展的数据结构，通常是不连续的内存区域。这是由于系统使用链表来存储空闲内存地址的，因此堆区的内存分配可能是不连续的。
    栈区：
    空间大小：栈区的大小通常由系统预先规定好，并且相对较小。在Windows系统中，栈的大小通常是2MB（或1MB，取决于编译器的设置）。
    扩展方向：栈区是向低地址扩展的数据结构，是一块连续的内存区域。当栈上的内存空间不足时，会发生栈溢出错误。
    **（即堆区内存大，不连续；栈区内存小，连续）**
    3. 数据结构与访问速度
    堆区：
    数据结构：堆区中的数据结构可以是任意的，由程序员自行定义和管理。
    访问速度：由于堆区是不连续的内存区域，并且需要程序员手动管理内存，因此访问堆区数据的速度相对较慢。此外，堆区还容易产生内存碎片，进一步影响访问速度。
    栈区：
    数据结构：栈区通常被实现为先进后出（LIFO）的数据结构，即栈。
    访问速度：由于栈区是连续的内存区域，并且由系统自动管理内存，因此访问栈区数据的速度相对较快。
    **（即堆区数据结构任意，访问速度满；栈区为栈结构，访问速度快些）**
    4. 生命周期与作用域
    堆区：
    生命周期：堆区数据的生命周期**由程序员控制**。程序员需要在适当的时候释放已分配的内存，否则可能会导致内存泄漏。
    作用域：堆区数据的作用域是**全局的或跨函数的**，只要程序员不释放内存，数据就可以一直存在。
    栈区：
    生命周期：栈区数据的生命周期**与函数的执行周期相同**。当函数被调用时，栈区数据被创建；当函数执行完毕并返回时，栈区数据被销毁。
    作用域：栈区数据的作用域是局部的，仅限于**函数内部或函数调用的上下文中**。
3. 程序运行过程中，内存模型当中的哪些区是只读的，哪些区是可读写的？
内存模型中的代码区和常量区是只读的，而全局数据区（包括已初始化数据区和未初始化数据区）、堆区和栈区则是可读写的
4. 如何使用malloc()、free()函数，它们针对的哪一个区进行操作？
   对堆区进行操作
5. 为什么要对程序使用的内存进行管理？
   1. 资源优化：
内存是有限的：计算机系统中的物理内存（RAM）是有限的。有效的内存管理可以确保程序在需要时能够获得足够的内存，同时避免不必要的内存浪费。
提高性能：通过合理的内存分配和释放，可以减少内存碎片，提高内存访问速度，从而优化程序的性能。
   2. 避免内存泄漏：
内存泄漏是指程序在分配内存后未能正确释放，导致这些内存永远无法被再次使用。长期存在的内存泄漏会耗尽系统资源，导致程序崩溃或系统变得不稳定。
   3. 防止野指针：
野指针是指指向已释放内存或未分配内存的指针。使用这些指针进行内存访问会导致未定义行为，可能引发程序崩溃或数据损坏。通过有效的内存管理，可以避免野指针的出现。
   4. 支持多任务处理：
在多任务操作系统中，多个程序可能同时运行。有效的内存管理可以确保每个程序都能获得其所需的内存资源，同时防止程序之间互相干扰。
   5. 数据安全和完整性：
正确的内存管理可以防止数据被意外覆盖或损坏。例如，通过避免缓冲区溢出等内存错误，可以保护敏感数据不被泄露或篡改。
    6. 符合编程规范：
遵循良好的内存管理实践是编写高质量代码的重要部分。这包括使用适当的内存分配和释放函数、避免内存泄漏和野指针等问题，以及确保内存访问的合法性和安全性。
    7. 可移植性和兼容性：
不同的操作系统和硬件平台对内存管理的要求可能有所不同。通过遵循通用的内存管理原则和实践，可以编写出更具可移植性和兼容性的代码。
## 内存模型的应用
1. constValue
存储区域：**常量区**
原因：constValue是一个全局常量，它在程序的整个生命周期内都存在，且其值不能被修改。因此，它存储在静态存储区的全局/静态数据部分，与全局变量共享相同的内存区域，但由于它是常量，所以它的值在编译时就确定了，并且在运行时不能被改变。
1. constString
存储区域：**常量区**
原因：constString是一个指向常量字符串的指针。字符串字面量（"Hello, World!"）在编译时被存储在常量数据区，这个区域用于存储程序中的常量值。由于字符串字面量本身也是常量，所以它们不能被修改。constString变量本身（即指针）存储在全局/静态数据区，但它指向的是常量数据区的字符串。
1. globalVar
存储区域：静态存储区（静态数据区，**全局数据区**的一种）
原因：globalVar是一个全局变量，它在程序的整个生命周期内都存在，且可以在程序的任何地方被访问和修改。因此，它存储在静态存储区的全局/静态数据部分。
1. staticVar
存储区域：静态存储区（静态数据区，**全局数据区**的一种）
原因：staticVar是一个静态局部变量，虽然它是在main函数内部定义的，但由于使用了static，它的生命周期被延长到了程序的整个运行期间。虽然它在main函数内部可见，但像全局变量一样，它存储在静态存储区的全局/静态数据部分。
**这里我对静态储存区有点疑惑（虽然静态存储区有时也包含常量（如用static关键字修饰的常量），但它与专门的常量区是有区别的。常量区通常用于存储那些在编译时就已确定其值并且在程序运行期间不会被修改的常量（如字符常量、字符串常量等）。而静态存储区则更多地用于存储需要在程序运行期间保持其值的变量和数据。不知道这样理解对不对）**
1. localVar（在function中定义）
存储区域：**栈区**
原因：localVar是一个局部变量，它在function函数被调用时创建，在函数返回时销毁。在函数外是无法调用的，局部变量通常存储在栈区，这是一个后进先出（LIFO）的内存区域，用于存储函数调用时的临时数据。
1. ptr（在function中定义）
存储区域：**栈区（指针变量本身），堆区（指针指向的内存）**
原因：ptr是一个指向int类型的指针变量，它本身存储在栈区。但是，它指向的内存是通过malloc函数在堆区动态分配的。因此，ptr变量本身（即指针）的存储位置在栈区，而它指向的内存块在堆区。
1. localVarMain
存储区域：**栈区**
原因：localVarMain是main函数中的一个局部变量，与localVar类似，它在main函数被调用时创建，在函数返回时销毁。因此，它也存储在栈区。
**输出的各变量地址（但好像看不出来在哪个区，也有可能是我的问题）**
[![pAtjFuF.png](https://s21.ax1x.com/2024/10/15/pAtjFuF.png)](https://imgse.com/i/pAtjFuF)
## 浅谈Cache
1. 
- 冯诺伊曼体系结构：
冯·诺依曼结构也称普林斯顿结构，是一种将程序指令存储器和数据存储器合并在一起的存储器结构。程序指令存储地址和数据存储地址指向同一个存储器的不同物理位置，因此程序指令和数据的宽度相同。数学家冯·诺依曼提出了计算机制造的三个基本原则，即采用二进制逻辑、程序存储执行以及计算机由五个部分组成（运算器、控制器、存储器、输入设备、输出设备），这套理论被称为冯·诺依曼体系结构。
[![pAt54z9.webp](https://s21.ax1x.com/2024/10/15/pAt54z9.webp)](https://imgse.com/i/pAt54z9)
- 现代计算机的组织结构：
现代计算机的组织结构主要涉及计算机的各个组成部分如何协同工作以实现计算机的功能。它包括了计算机的中央处理器（CPU，由运算器和控制器组成）、内存（主存储器）、输入/输出（I/O）设备等各个部分的组织方式。现代计算机已经发展为以存储器为中心，使I/O操作尽可能地绕过CPU直接在设备和存储器之间完成，以提高系统的整体运行效率。
- 两者的不同点：
  - 中心不同：早期的冯诺依曼机以**运算器为中心**，输入/输出设备通过运算器与存储器传送数据；而现代计算机的组织结构则以**存储器为中心。**
  - 数据传送方式不同：冯诺依曼体系结构中，CPU需要从存储器取出指令和数据进行相应的计算；而在现代计算机的组织结构中，I/O操作可以绕过CPU直接在设备和存储器之间完成。
2. 主存储器的工作原理
主存储器一般采用半导体存储芯片实现，其工作原理是通过电子元件的导通和截止状态来表示二进制数据的0和1。当计算机需要读取存储器中的数据时，会根据地址线指定的地址，将存储器中对应地址的数据传输到数据线上。而当计算机需要写入数据到存储器时，同样会根据地址线指定的地址，将数据线上的数据写入到对应地址的存储单元中。
3. 什么是Cache的局部性原理？它包括哪些方面的内容？
- Cache的局部性原理：
Cache的局部性原理指的是将程序中最活跃、运行最频繁的一部分放在Cache中去。这是因为在程序执行过程中，某些数据和指令会被频繁地访问，而将这些数据和指令放在速度更快的Cache中可以显著提高程序的执行效率。
Cache的局部性原理包括的内容：
- + 时间局部性：在最近的未来要用到的信息，很可能是现在正在使用的信息。即如果某个数据被访问过一次，那么不久的将来它可能再次被访问。
  + 空间局部性：在最近的未来要用到的信息（指令和数据），很可能与现在正在使用的信息在存储空间上是邻近的。即如果某个数据被访问了一次，那么与它相邻的数据也可能很快被访问。
4. Cache的运用为什么可以加快系统整体性能
Cache即高速缓冲储存器，是为了消除告诉的CPU与主储存器之间的速度差而放置在CPU与主储存器的缓冲储存器（这段话是c语言程序设计书上抄来的（））
Cache的运用可以加快系统整体性能，主要是因为Cache具有高速存取数据的能力，并且利用了程序的局部性原理。当CPU需要读取数据时，它首先在Cache中查找是否有所需内容。如果CPU需要访问的内容大多能在Cache中找到（称为访问命中），则可以大大减少访问主存储器的次数，从而显著提高系统性能。因为主存储器的存取速度相对较慢，而Cache的存取速度则快得多，所以通过提高Cache的命中率，可以显著降低CPU的等待时间，加快程序的执行速度。
## 代码优化
由于常量区的访问速度大于一般变量，堆区速度大于栈区，故进行如下优化（因为没给源程序进行优化，所以就用题目上面的代码自行改编一下了，不知道算不算完成任务，但是想不出其他的了qwq）
**优化前的代码**
```c
#include <stdio.h>
#include <stdlib.h>
int globalVar = 10;
void function(int arg)
{
    int localVar = 20;
    int *ptr = (int*)malloc(sizeof(int));
    *ptr = 30;
    printf("%p\n",ptr);
    printf("%d\n",*ptr);
    free(ptr);
}
int main()
{
	int constValue = 100;
	char* constString = "Hello, World!";
    static int staticVar = 40;
    int localVarMain = 50;
    function(60);
    printf("%s\n",constString);
    printf("%p\n",constString);
    printf("%d\n",constValue);
    printf("%d\n",staticVar );
    printf("%d\n",constValue);
    return 0;
}
```
运行截图[![pAtxkk9.png](https://s21.ax1x.com/2024/10/15/pAtxkk9.png)](https://imgse.com/i/pAtxkk9)
**优化后的代码**
```c
#include <stdio.h>
#include <stdlib.h>
int globalVar = 10;
const int constValue = 100;
const char* constString = "Hello, World!";
const int staticVar = 40;
int *ptr = (int*)malloc(sizeof(int));
void function(int arg)
{
    int localVar = 20;
    *ptr = 30;
    printf("%p\n",ptr);
    printf("%d\n",*ptr);
    free(ptr);
}
int main()
{
    int localVarMain = 50;
    function(60);
    printf("%s\n",constString);
    printf("%p\n",constString);
    printf("%d\n",constValue);
    printf("%d\n",staticVar );
    printf("%d\n",constValue);
    return 0;
}
```
运行截图[![pAtxel6.png](https://s21.ax1x.com/2024/10/15/pAtxel6.png)](https://imgse.com/i/pAtxel6)
好像确实快了那么一丢丢哈哈哈哈