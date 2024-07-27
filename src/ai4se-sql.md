# SQL 优化生成

## 示例

### Text2SQL

### Text to SPL

[日志易 Text to SPL 探索](https://mp.weixin.qq.com/s/maEWbNBUhNaO0_WwfmSEPw)

![](images/ali-system-spl.png)

```jflex
<data-source> | <spl-expr> ... | <spl-expr> ...
```

[SLS 查询新范式：使用 SPL 对日志进行交互式探索](https://www.cnblogs.com/alisystemsoftware/p/18151174)

> SPL 即 SLS Processing Language，是 SLS 对日志查询、流式消费、数据加工、Logtail 采集、以及数据 Ingestion
> 等需要数据处理的场景，提供的统一的数据处理语法，这种统一性使得 SPL 可以在整个日志处理的生命周期内，实现 "Write Once，Run
> Anywhere" 的效果。

![](images/spl-arch.png)

< spl-expr >是 SPL 指令，支持正则取值、字段分裂、字段投影、数值计算等多种操作，具体参考 SPL 指令介绍。

