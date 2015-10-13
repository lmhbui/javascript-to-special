#商品排序
- [排序功能](#排序功能)

#排序功能
1.请求地址
```
/event/sort
```
2.请求参数
```js
{
  ids: ids, //商品ids
  eid: eid //专场id
}
```
3.返回结果
```js
{
ids:20000014,
eid:147
}
```

4.示例
```js
$.post('/event/sort', {
  ids: ids,
  eid: eid
});
```
