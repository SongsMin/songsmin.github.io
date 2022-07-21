## 松松🐿‘s blog

### Open Source OS Training 2022 - Weekly

#### W2(20220718 - 20220724)

- targets

  学习 RISC-V 体系，做实验。

- daily

  - 2022-07-21

    重读《计算机组成与设计》第二章，补 RISC-V 寄存器相关约定

    | 寄存器         | 约定                                                         |
    | -------------- | ------------------------------------------------------------ |
    | x0             | 硬连线为0                                                    |
    | x1             | 返回地址（return address, ra）寄存器，jal x1, ProcedureAddress |
    | x2             | 栈指针（stack pointer, sp）寄存器                            |
    | x3             | 全局指针（global pointer, gp）寄存器                         |
    | x4             | 线程指针（thread pointer, tp）寄存器                         |
    | x5~x7, x28~x31 | 临时寄存器，在过程调用中不被调用者保存                       |
    | x8~x9, x18~x27 | 保存寄存器（saved register），在过程调用中必须被保存（一旦使用，由被调用者保存并恢复） |
    | x10~x17        | 参数寄存器，用于传递参数或返回值                             |
    | x8（非必须）   | 帧指针（frame pointer, fp），一些编译器使用                  |

    | 名称    | 寄存器号 | 用途                   | 调用时是否保存 |
    | ------- | -------- | ---------------------- | -------------- |
    | x0      | 0        | 常数0                  | --             |
    | x1      | 1        | 返回地址（链接寄存器） | 是             |
    | x2      | 2        | 栈指针                 | 是             |
    | x3      | 3        | 全局指针               | 是             |
    | x4      | 4        | 线程指针               | 是             |
    | x5~x7   | 5~7      | *临时*                 | ***否***       |
    | x8~x9   | 8~9      | 保存                   | 是             |
    | x10~x17 | 10~17    | 参数/结果              | ***否***       |
    | x18~x27 | 18~27    | 保存                   | 是             |
    | x28~x31 | 28~31    | *临时*                 | ***否***       |

    回顾 lab0-1，好理解多了。

  - 2022-07-20
  
    lab0-1 由于 asm 宏通不过不知道该怎么处理卡住了，在群里大佬的指导下不再本地 overwrite riscv 包解决了。
  
    阅读完 OS 实验指导第二章，发现需要补一些 RISC-V 基础，加深对各寄存器的认识。
  
    前几天比较忙，断了几天。

#### W1 (20220711 - 20220717)

- targets

  复习计算机组成原理，学习 RISC-V 体系，搭环境，完成实验。

- daily

  - 2022-07-15

    继续阅读 OS 实验指导第二章。较忙。

  - 2022-07-14

    继续阅读 OS 实验指导第二章，对照 lab0-1 代码进行理解。

    阅读洛佳大佬《使用 Rust 编写操作系统》系列前两篇，对照 OS 实验指导前两章加深理解。
  
    阅读 《The Rust Reference》Inline assembly 章节，了解 asm 宏用法。
  
  - 2022-07-13
  
    lab0-1，make run，阅读 OS 实验指导第二章引言与实现应用程序部分，对照项目代码进行理解。
  
    阅读《计算机组成与设计》。
  
  - 2022-07-12
  
    参照 OS 实验指导第一章内容，从 cargo new 起自己实现一遍构建环境。
  
    链接脚本和 entry.asm 完全照搬，需要后续了解一下语法以及发生了什么。
  
  - 2022-07-11
  
    lab0-0，设置环境并尝试跑起来。
  
    分别在 codespace 和本地 Ubuntu (on WSL2) 各搭了一遍，查看 Makefile，对比精简 OS 实验指导第 0 章了解基本环境。
  
    阅读《计算机组成与设计》前两章，上 B 站看浙大课程。
  
    依然比较懵，qemu 不咋会用，去年尝试自己玩的时候用 qemu for windows 并没有跑起来，现在在 ubuntu 上跑起来了还没搞明白为啥。边实践边学吧。
  

#### W0 (20220705 - 20220710)

- targets

  刷 rustlings，复习 rust 基础  
  | Exercise               | Book Chapter | Done |
  | ---------------------- | ------------ | ---- |
  | variables              | §3.1         | √    |
  | functions              | §3.3         | √    |
  | if                     | §3.5         | √    |
  | move_semantics         | §4.1         | √    |
  | primitive_types        | §4.3         | √    |
  | structs                | §5.1         | √    |
  | enums                  | §6           | √    |
  | modules                | §7           | √    |
  | collections            | §8.1, §8.3   | √    |
  | strings                | §8.2         | √    |
  | error_handling         | §9           | √    |
  | generics               | §10          | √    |
  | option                 | §10.1        | √    |
  | traits                 | §10.2        | √    |
  | tests                  | §11.1        | √    |
  | standard_library_types | §13.2        | √    |
  | threads                | §16.1        | √    |
  | macros                 | §19.6        | √    |
  | clippy                 | n/a          | √    |
  | conversions            | n/a          | √    |
  | advance_errors         | n/a          | √    |

- daily

  - 2022-07-10

    周末休息 ```(*^_^*)``` 淘二手《计算机组成与设计：硬件/软件接口 RISC-V 版》
  
  - 2022-07-09
  
    rustlings - 完成 standard_library_types(Box, Arc, Iter), threads(Arc and Mutex), macros, clippy, conversions, advance_errors 练习，当前所有 rustlings 均已完成。
  
    Box 是一种把“内容”丢到堆上的智能指针，常用于举例的一个应用场景是链表结构。扩展阅读：双向链表与 Weak 智能指针。
  
    Arc/Rc，引用计数智能指针，Arc impl 了 Send 可用于线程间，生命周期结束后引用计数 -1。
  
    Mutex/RwLock，带锁智能指针，生命周期结束后解锁，类似 Java AutoClosable，通过 rust 的生命周期管理更不易错。注意同一个 Mutex 在同一线程内重复 lock 会死锁。
  
    ```From<T> for U``` impl 了 ```Into<U> for T```，同理 ```TryFrom<T> for U``` impl 了 ```TryInto<U> for T```，因此如非必要写 From/TryFrom 就行了，Into/TryInto 自动完成。
  
    advance_errors 通过实现 From trait 把手动 Result<T, E1>.map_err(e1_to_e2)? 简化了。另外 error handle 可以参考 [thiserror](https://github.com/dtolnay/thiserror) 和 [anyhow](https://github.com/dtolnay/anyhow) 两个库。
  
    rust 复习暂时告一段落，重点先转移到 OS 学习。
  
  - 2022-07-08
  
    rustlings - 完成 generics, option, traits, tests 练习。
  
    今天下班太晚，只练了半小时。明天争取收尾 rustlings。
  
  - 2022-07-07
  
    rustlings - 完成 structs, enums, modules, vec, hashmap, strings, errors 练习。
  
    errors 忘太快，深刻复习了一遍。
  
  - 2022-07-06
  
    rustlings - 安装 rustlings 并熟悉用法，完成 intro, variables, functions, if, move_semantics, primitive_types 练习。
  
    - move_semantics2
  
      hint 提示三种方法，提供一个 copy 给 ```fill_vec``` 避免所有权转移、改为传 borrow 在 ```fill_vec``` 内生成一个副本、改为传 mutable borrow 在 ```fill_vec``` 内直接改（但不返回，同时会造成 ```vec0``` 被改变）。
  
      第三种尚未实验。
  
    - primitive_types3
  
      题目本意是数组类型，但注意到 ```ExactSizeIterator``` trait 同样具有 ```len``` 方法，某些 ```Range```/```RangeInclusive``` 同样可以通过编译。
  
      练习时发现直接
  
      ```rust
      let a = 0..=99;
      if a.len() >= 100 {
          ...
      }
      ```
  
      无法通过编译，报错提示 ```RangeInclusive<i32>``` 未实现 ```ExactSizeIterator``` trait，而 ```RangeInclusive<i16>``` 等进行了实现，查阅了标准库 iter/range.rs 部分代码后了解到是由于 ```ExactSizeIterator::len``` 返回类型是 ```usize```，为防止越界而未对可能越界的数字类型进行 impl。
  
      同时也注意到，在 16 位平台下，```Range<u32>```、```Range<i32>```、```RangeInclusive<u16>```、```RangeInclusive<i16>``` 依然可能产生越界问题，在实践中应注意。
