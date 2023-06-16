<span style="font-size:26px;font-weight:bold;">一些JS原生属性方法的测试demo集合</span>

- [entries()、keys()、values()数组、对象遍历](#entrieskeysvalues数组对象遍历)
- [过滤范围](#过滤范围)
- [原位（in place）过滤范围](#原位in-place过滤范围)
- [降序排列](#降序排列)
- [复制和排序数组](#复制和排序数组)
- [创建newCalculator](#创建newcalculator)
- [创建 new Accumulator](#创建-new-accumulator)
- [创建一个可扩展的 calculator](#创建一个可扩展的-calculator)
- [映射到 names](#映射到-names)


#### entries()、keys()、values()数组、对象遍历

<img src="./README/README/1.png" alt="1" style="max-width: 67%!important;" />

#### 过滤范围

>   写一个函数 `filterRange(arr, a, b)`，该函数获取一个数组 `arr`，在其中查找数值大于或等于 `a`，且小于或等于 `b` 的元素，并将结果以数组的形式返回。
>
>   该函数不应该修改原数组。它应该返回新的数组。

```js
let arr = [5, 3, 8, 1];

let filtered = filterRange(arr, 1, 4);

console.log( filtered ); // 3,1（匹配值）
console.log( arr ); // 5,3,8,1（未修改）
```

#### 原位（in place）过滤范围

写一个函数 `filterRangeInPlace(arr, a, b)`，该函数获取一个数组 `arr`，并删除其中介于 `a` 和 `b` 区间以外的所有值。检查：`a ≤ arr[i] ≤ b`。

该函数应该只修改数组。它不应该返回任何东西。

```js
let arr = [5, 3, 8, 1];

filterRangeInPlace(arr, 1, 4); // 删除了范围在 1 到 4 之外的所有值

alert( arr ); // [3, 1]
```

#### 降序排列

```js
let arr = [5, 2, 1, -10, 8];

// ……你的代码以降序对其进行排序

alert( arr ); // 8, 5, 2, 1, -10
```

排序时,sort() 方法会调用该表达式,并传入数组的两个元素作为 *a* 和 *b* 。

表达式需要返回一个负数、0 或正数,来告知 sort() 方法元素的排序顺序:

- 返回负数,则 *a* 排在 *b* 前面
- 返回正数,则 *b* 排在 *a* 前面
- 返回 0 ,则相对位置不变

#### 复制和排序数组

我们有一个字符串数组 `arr`。我们希望有一个排序过的副本，但保持 `arr` 不变。

创建一个函数 `copySorted(arr)` 返回这样一个副本。

```js
let arr = ["HTML", "JavaScript", "CSS"];

let sorted = copySorted(arr);

alert( sorted ); // CSS, HTML, JavaScript
alert( arr ); // HTML, JavaScript, CSS (no changes)
```

>   考察点：数组的`slice()`方法，我们可以不带参数地调用它：`arr.slice()` 会创建一个 `arr` 的副本。其通常用于获取副本，以进行不影响原始数组的进一步转换。

#### 创建newCalculator

创建一个构造函数 `Calculator`，它创建的对象中有三个方法：

-   `read()` 使用 `prompt` 请求两个值并把它们记录在对象的属性中。
-   `sum()` 返回这些属性的总和。
-   `mul()` 返回这些属性的乘积。

例如：

```js
let calculator = new Calculator();
calculator.read();

alert( "Sum=" + calculator.sum() );
alert( "Mul=" + calculator.mul() );
```

#### 创建 new Accumulator

创建一个构造函数 `Accumulator(startingValue)`。

它创建的对象应该：

-   将“当前 value”存储在属性 `value` 中。起始值被设置到构造器 `startingValue` 的参数。
-   `read()` 方法应该使用 `prompt` 来读取一个新的数字，并将其添加到 `value` 中。

换句话说，`value` 属性是所有用户输入值与初始值 `startingValue` 的总和。

下面是示例代码：

```js
let accumulator = new Accumulator(1); // 初始值 1

accumulator.read(); // 添加用户输入的 value
accumulator.read(); // 添加用户输入的 value

alert(accumulator.value); // 显示这些值的总和
```

#### 创建一个可扩展的 calculator

创建一个构造函数 `Calculator`，以创建“可扩展”的 calculator 对象。

>   -   obj[prop] : 当 prop 是一个变量时,需要使用 `[]` 访问
>   -   obj.prop : 当 prop 是一个确定属性名时,可以直接使用 `.` 访问

>   **构造函数特点:**
>
>   `new Fn()：`
>
>   构造函数内部会创建一个新的对象，即 `Fn` 的实例
>
>   函数内部的 `this` 指向 新创建的 `Fn` 的实例
>
>   默认的返回值是 `Fn` 的实例

该任务由两部分组成。

1.  首先，实现 `calculate(str)` 方法，该方法接受像 `"1 + 2"` 这样格式为“数字 运算符 数字”（以空格分隔）的字符串，并返回结果。该方法需要能够理解加号 `+` 和减号 `-`。

    用法示例：

    ```javascript
    let calc = new Calculator;

    alert( calc.calculate("3 + 7") ); // 10
    ```

2.  然后添加方法 `addMethod(name, func)`，该方法教 calculator 进行新操作。它需要运算符 `name` 和实现它的双参数函数 `func(a,b)`。

    例如，我们添加乘法 `*`，除法 `/` 和求幂 `**`：

    ```javascript
    let powerCalc = new Calculator;
    powerCalc.addMethod("*", (a, b) => a * b);
    powerCalc.addMethod("/", (a, b) => a / b);
    powerCalc.addMethod("**", (a, b) => a ** b);
    
    let result = powerCalc.calculate("2 ** 3");
    alert( result ); // 8
    ```

-   此任务中没有括号或复杂的表达式。
-   数字和运算符之间只有一个空格。
-   你可以自行选择是否添加错误处理功能。

#### 映射到 names

你有一个 `user` 对象数组，每个对象都有 `user.name`。编写将其转换为 names 数组的代码。

例如：

```js
let john = { name: "John", age: 25 };
let pete = { name: "Pete", age: 30 };
let mary = { name: "Mary", age: 28 };

let users = [ john, pete, mary ];

let names = /* ... your code */

alert( names ); // John, Pete, Mary
```

>   方法一：
>
>   for…of…循环输出user并将user.name存入names数组
>
>   方法二：
>
>   使用map()方法遍历users，并将每一项循环的user.name返回并存入names数组
