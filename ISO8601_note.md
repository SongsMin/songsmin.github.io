# ISO 8601:2019 笔记

## 难懂/易混淆术语

- time scale

  时间标度，以某时刻为原点的、在时间轴上描述时刻的有序标记系统。

  不要简单理解成不同缩放比，不同原点也同样是不同的 time scale。

  - clock
  - calendar

- instant

  时刻，时间轴上的点

- time

  在 time scale 上描述时刻或时段的标志

- date

  calendar 尺度上的 time

- time interval

  时段，两个 instant 之间，时间轴上的段，有坐标

- recurring time interval

  循环时段

- duration

  时长，无坐标，时段的长度

- time scale unit

  unit of measurement of a duration，时长的测量单位

- second/minute/hour

  duration 时长，second 为时长的基准

- clock second/minute/hour

  time scale unit 时长测量**单位** 

- day/week/month/year

  duration

- calendar day/week/month/year

  time scale unit

- decade/century

  time scale unit

- calendar day of week/calendar day of month/calendar day of year/calendar week of year

  ordinal number，XX 的第几 X。

  注意到没有专门的 calendar year of era 和 calendar month of year，大约是由于不会产生歧义。

  同时注意到各 time scale unit 也同时具有该单位下 ordinal number 的表述意义。

- x date

  不同方式表述的指定 calendar day

- calendar date

  年-月-日，calendar year + calendar month + calendar day of month

- ordinal date

  年-第几天，calendar year + calendar day of year

- week date

  年-第几周-周几，calendar year + calendar week of year + calendar day of week，第一周是本年第一个周四所在的周。

  注意到“年-月-月的第几周-周几”并不是一种标准内的 x date，类似父亲节/母亲节无法使用标准表述，需要 extensions 扩展的表述方式。

- date and time expression/representation

  - representation - ```[YYYY]["-"][MM]["-"][DD]```
  - expression - ```2022-07-19``` is an expression to the representation above.

- time scale component

  date and time expression/representation 中的一个 time scale unit 的表述。

  "x component" is short for "time scale component x".