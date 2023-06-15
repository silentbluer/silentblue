### 一些JS原生属性方法的测试demo集合

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
