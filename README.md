编程之路
===

>记录编写过程中记忆深刻的问题或痛彻后的感悟，问题或大或小。

>大致是从2009年开始，遗憾的是每条记录没有标明具体时间点。


1. JS 不支持数组自动定义，eg. `var arr = []; arr[0][]` 将抛出未定义错误

2. JS 数组长度的统计依据数字索引的最大值, 非数字索引元素不记在内

3. JS 中, `Array(4)` 将构造长度为`4`的数组; PHP 中, 将构造长度为`1`的数组

4. JS 中, `new` 操作符可省略的情况仅限于内置对象的实例化; AS 中, 自定义对象亦可省略

5. PHP 与 JS中, `\s`只匹配空格(C风格中，`\s`匹配`\t\v\f\r\n`; PERL5已将`\v`从`\s`容器中移除)

6. 一般情况下, 定义`constructor`属性仅仅为了曝露该类的接口, 这里面牵扯到一个标准约束的问题; 考虑`instanceof`的情况

7. `new`: 自顶向下拷贝原型对象

8. 以绑定的角度去审视this关键字指向的对象, 就很简单了

9. `var arr = []; var s = arr;` s为指向arr的引用

10. `this`仅适用于其所处的`function`域

11. 重写某函数可用如下模板: 
  <pre>
	Function.prototype.override = function() {
		var fn = this, 
			args = Array.slice(arguments);
		return function() {
			// do your tricks
			fn.apply(this, args.concat(Array.slice(arguments)));
		}
	};
	fn = function(a, b, c, d, e);
	var f = fn.override(1, 2, 3);
	f(4);
  </pre>
    
12. JS中, 引用对应更新，而非赋值

13. 程序设计即确定产品如何被使用的过程

14. 脚本对象的可交互性可作为安全编码的重要指标 假设在不修改源码的情况下, 通过代码注入或者第三方工具修改程序内部机制的可能性与程序的安全性成反比

15. 面对复杂场景，不去追求细节而只关注单元

16. 如何在链式调用与过程调用中选择? 可参照以下两点: 
    >- 优先考虑链式调用
    >- 链式调用与过程调用应可轻易转换且无重复代码
    
17. 遍历数组时, 若删除数组元素, 键不会被重置

18. `var fun = function() {} 与 function fun() {}` 的区别: 
    >- 匿名与实名
    >- 运行时与编译
    
19. `o instanceof f`: 
    >- `if f.prototype is not one of the values in the prototype chain of o, then o is not an instance of f`.
    >- `instanceof considers the "superclasses"`.
    >- 关键词: "原型对象"

20. 闭包对应函数

21. JS中, 对象与原型对象为同一事物

22. `constructor`: 
    >- 第三方可由此访问到类的`prototype`属性
    
23. `Array.prototype.concat`方法不强制转换"类数组"

24. 大胆可行的想法与上乘优质的产出成正比

25. 正确的事情都是顺理成章的事情(好的设计都是水到渠成)

26. 计算机永远不会欺骗你

27. `Sequentially`展示了变体函数的编程方法: 元函数 + 规则 = 变体函数

28. `MVar`提供了在异步环境中同步数据流的方法

29. `code path count`

30. 使用`do while`循环的技巧: 在`do`里面明确退出

31. 迭代三要素: 结果, 最小单元, 条件; 若操作引用, 则无需返回结果

32. PHP中无闭包, 可通过`static`到达相同效果 

33. 不要"绞尽脑汁"的时候去创作, 选择正确的点很重要

34. 外围闭包不应作为判断条件, 这将导致内围程序难以维护, 且容易出错

35. 巅峰之作常常难以超越, 请尽量把一件事情做好

36. 你经常会碰到一种情况: 你不断尝试给自己解释曾经已很好地解释过的问题; 你应当再做一件事: 记录你设计的应用场景及问题

38. 避免代码重复现象的唯一方法是持久重构

39. 适配模式四步曲: 执行接口(`api`), 验证(`valid`), 构造对象(`extend`), 实例化(`init`)

40. `get set`使用技巧: 被操作的属性链接至内部实质保留值的对应属性

41. 适度性与差异性: 程序设计中, 你应当总是关注最核心的要传递给用户的"价值", 而非过度地完善次要功能; 
比如, 同一个函数在不同的环境, 其提供的功能可能存在差异性, 这是完全合理的

42. 不要提前预想

43. 在一个事件流中, 全程共享同一事件对象(`2014-09`)

44. 在一个事件流中, 异步流在该事件流及其触发的关联事件流最末端执行, 最常见的场景莫过`blur`与`focus`(`2014-09`) 

45. 浏览器中的js是单线程的, 没有并行执行能力; 而异步编程, 本质上属于流程控制(`2014-09`)

46. 违背常理的现象一定是假象(`2014-09`)

47. 区分循环与迭代, 迭代的显著特征是单元之间有依赖关系

48. Write your code in generators, promises, or unnested callbacks and you'll be fine.(`2015-10-29`)

49. 设计UI控件，结构是`可以做到`剥离的(`2016-02-03`)

50. 设计方法是关注小单元，忽略大框架；本质上没有大框架这类东西(`2016-02-03`)

51. 目前看来，JS中没有`concurrent`这个词(`2016-04-10`)

52. yield本质上解决的是前后依赖的异步任务的同步流程控制问题(`2016-04-10`)

53. 宏观编程不等于高阶编程，而是你在处理一个任务时的思维方式。宏观编程往往能够化繁为简，让你处于最正确的那个点上。(`2016-10-11`)

54. 强类型语言只维护一份静态模版；好处是节约时间，坏处是浪费空间。(`2017-05-07`)

55. Ruby 中的 EventMachine && Fiber 对等 Node.js 中的 EventLoop && Generators (`2017-09-16`)

56. 如果你问遍整个世界都找不到答案，那么此错误可能非彼错误(`2018-04-09`)
