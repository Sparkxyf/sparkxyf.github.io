# MySQL面试

1. 如果表 T 中没有字段 k，而你执行了这个语句 select * from T where k=1, 那肯定是会报“不存在这个列”的错误： “Unknown column ‘k’ in ‘where clause’”。你觉得这个错误是在我们上面提到的哪个阶段报出来的呢？

   debug模式下：Complete optimizer trace

   《高性能mysql》里提到解析器和预处理器。 解析器处理语法和解析查询, 生成一课对应的解析树。 预处理器进一步检查解析树的合法。比如: 数据表和数据列是否存在, 别名是否有歧义等。如果通过则生成新的解析树，再提交给优化器。

2. 