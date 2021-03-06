<!-- YAML
added: v0.1.25
-->

* `obj` {Object} 要序列化为 URL 查询字符串的对象。
* `sep` {string} 用于在查询字符串中分隔键值对的子字符串。**默认值:** `'&'`。
* `eq` {string} 用于在查询字符串中分隔键和值的子字符串。**默认值:** `'='`。
* `options`
  * `encodeURIComponent` {Function} 当将查询字符串中不安全的 URL 字符转换为百分比编码时使用的函数。**默认值:** `querystring.escape()`。

`querystring.stringify()` 方法通过遍历对象的自身属性从给定的 `obj` 生成 URL 查询字符串。

它会序列化传入的 `obj` 中以下类型的值：{string|number|boolean|string[]|number[]|boolean[]}。
任何其他的输入值都将会被强制转换为空字符串。

```js
querystring.stringify({ foo: 'bar', baz: ['qux', 'quux'], corge: '' });
// 返回 'foo=bar&baz=qux&baz=quux&corge='

querystring.stringify({ foo: 'bar', baz: 'qux' }, ';', ':');
// 返回 'foo:bar;baz:qux'
```

默认情况下，查询字符串中需要进行百分比编码的字符将会被编码为 UTF-8。
如果需要其他的编码，则需要指定其他的 `encodeURIComponent` 选项：


```js
// 假设 gbkEncodeURIComponent 函数已存在。

querystring.stringify({ w: '中文', foo: 'bar' }, null, null,
                      { encodeURIComponent: gbkEncodeURIComponent });
```

