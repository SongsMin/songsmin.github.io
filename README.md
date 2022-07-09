## 松松🐿‘s blog

### Open Source OS Training 2022 - Weekly

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
