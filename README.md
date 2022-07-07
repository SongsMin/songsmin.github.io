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
  | generics               | §10          |      |
  | option                 | §10.1        |      |
  | traits                 | §10.2        |      |
  | tests                  | §11.1        |      |
  | standard_library_types | §13.2        |      |
  | threads                | §16.1        |      |
  | macros                 | §19.6        |      |
  | clippy                 | n/a          |      |
  | conversions            | n/a          |      |

- daily

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
