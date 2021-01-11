# proj2-os-kernels-by-history

### 项目描述
当前大学本科学生做OS实验面临工作量大，实验指导针对性不够强，难以对OS有整体理解等困难。为此，我们希望重新设计面向一般学生，能帮助他们
理解OS课程中各种概念的简洁明了的OS Kernels。同学们将发现，几百行高级语言为主编写的OS Kernel就能体现操作系统中各种抽象的概念。
设计实现这些简洁明了的OS Kernels的目的是：“给学生逐步设计实现OS的线索和参考实例，提高学生的OS分析能力和动手能力，强化学生对 OS 的整体观念”。
这一系列OS kernels的特点是：以CS发展的历史过程为导向，以满足应用需求为基准，实现相对独立，功能简单明确。

为此，我们采用了如下的规划思路：
- 在硬件方面，我们选择了便于OS设计实现的RISC-V硬件平台（基于虚拟硬件模拟器QEMU和物理硬件Kendryte K210（含MMU和S模式）；
- 在软件编程语言方面，我们选择了Rust和C编程语言，当然选择其它语言（Go,Nim,Swift, V-lang...）也是鼓励的。
- 在实验阶段上，大致仿照OS的发展历史来分阶段，每个OS kernel都算是一个历史阶段的OS的缩影，并有多个step组成，解决一两个明确的应用需求。
- 对实现的具体细节不限，只要能通过有明确操作系统服务接口描述的应用测实例即可算完成实验。

当前项目实现源码：
- （基于Rust语言）：https://github.com/rcore-os/rCore-Tutorial-v3
- （基于C语言）：https://github.com/DeathWish5/appdir

### 所属赛道

2021全国大学生操作系统比赛的“OS功能设计”赛道

### 参赛要求
- 以小组为单位参赛，最多三人一个小组，且小组成员是来自同一所高校的本科生（2021年春季学期或之后本科毕业的大一~大四的学生）
- 如学生参加了多个项目，参赛学生选择一个自己参加的项目参与评奖
- 请遵循“2021全国大学生操作系统比赛”的章程和技术方案要求

### 项目导师

吴一凡
- github https://github.com/wyfcyx
- email shinbokuow@163.com

### 难度

初等~中等

### 特征

- OS基于RISC-V SBI 规范（大大简化了驱动设计实现）
- 对类 Unix 操作系统有很好的参照
- 可完全使用 Rust 语言或C语言实现
- 支持 QEMU 仿真器（RISC-V）
- 支持 Kendryte K210（含MMU和S模式）

### 文档
- [从零开始基于 Rust 写 OS 的学习指导（无需 Rust 和 RISC-V 基础）](https://github.com/rcore-os/rCore/wiki/os-tutorial-summer-of-code)
- [中文实验指导](https://rcore-os.github.io/rCore-Tutorial-Book-v3/)
- [中文介绍ppt](rCore-Tutorial.pdf)

### 平台实现的注意事项

- Rust版本的OS kernels的不少组件 能库（Rust中的crates）的形式重用。
- 目前，在 QEMU 和 K210 平台上支持 CLINT 和 PLIC 外围设备。

### License

- GPL-3 license

## 预期目标

### 注意：下面的内容是建议内容，不要求必须全部完成。选择本项目的同学也可与导师联系，提出自己的新想法，如导师认可，可加入预期目标

在现有OS kernels的基础上，进一步完成如下目标OS kernels（编程语言不限；鼓励用Rust编程）：

### 第一题：支持虚存的换入换出功能

- 在QEMU（RV-64）和Kendryte K210开发板上，实现内存到 virtio-blk（qemu）和SD卡（K210开发板）上的换入换出；
- 实现各种页替换算法，并进行初步的性能比较；
- 撰写OS kernel设计与分析文档。

### 第二题：支持多核

- 在QEMU（RV-64）和Kendryte K210开发板上，支持多核，能够进行应用程序的并行处理；
- 实现用户态支持线程机制，有基本的线程管理相关的系统调用（线程创建，线程join，线程退出，线程互斥访问等）
- 实现多种内核同步互斥机制，并在内核中的不同模块应用这些同步互斥机制，实现高效率的并行；
- 撰写OS kernel设计与分析文档。

### 第三题：支持日志文件系统

- 在QEMU（RV-64）和Kendryte K210开发板上，实现一种日志文件系统；
- 能支持异常掉电和系统崩溃后的文件一致性；
- 文件系统有更加全面的文件访问能力（多级目录，硬链接等），支持多核并行方式处理，比单核情况下的性能要高；
- 撰写OS kernel设计与分析文档。

### 第四题：支持网络
- 在QEMU（RV-64）和Kendryte K210开发板上，实现简单的网络驱动（qemu：virtio；k210：有基于spi的wifi，类似串口等）和网络协议栈；
- 能支持基本的socket编程；
- 能运行简单的 Server，可以自己编写，也可以移植自著名开源实现 Nginx 等；
- 撰写OS kernel设计与分析文档。

### 第五题：体现OS各种功能、Bugs和跨硬件能力
- 实现目前没有实现的各种OS功能（如具有图形显示能力，支持树莓派，支持x86等）；
- 在QEMU（RV-64）和Kendryte K210开发板上，设计各种Bugs或更小粒度的steps，来帮助学生更好理解和完成各种OS kernel的实现；
- 实现OS kernel上的简化的lib库，并让更多的教学应用（如教学用的编译器，教学用网络协议栈，教学用算法/数据结构，教学用database等）能运行在这个OS kernel上；
- 撰写OS kernel设计与分析文档。

