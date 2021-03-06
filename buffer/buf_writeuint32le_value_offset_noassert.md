<!-- YAML
added: v0.5.5
-->

* `value` {Integer} 要写入 `buf` 的数值
* `offset` {Integer} 开始写入的位置，必须满足：`0 <= offset <= buf.length - 4`
* `noAssert` {Boolean} 是否跳过 `value` 和 `offset` 检验？**默认:** `false`
* 返回: {Integer} `offset` 加上写入的字节数

用指定的尾数格式（`writeUInt32BE()` 写入大尾数，`writeUInt32LE()` 写入小尾数）写入 `value` 到 `buf` 中指定的 `offset` 位置。
`value` 应当是一个有效的无符号的32位整数。
当 `value` 不是一个无符号的32位整数时，反应是不确定的。

设置 `noAssert` 为 `true` 则 `value` 的编码形式可超出 `buf` 的末尾，但后果是不确定的。

例子：

```js
const buf = Buffer.allocUnsafe(4);

buf.writeUInt32BE(0xfeedface, 0);

// 输出: <Buffer fe ed fa ce>
console.log(buf);

buf.writeUInt32LE(0xfeedface, 0);

// 输出: <Buffer ce fa ed fe>
console.log(buf);
```

