#商品排序

1.请求地址
```
/event/sort
```
2.请求参数
```js
{
ids[]:20000232
ids[]:20000279
ids[]:20000278
ids[]:20000233
eid:99
}
```
3.返回结果
```js
{
	"errorcode": 0,
	"message": "\u64cd\u4f5c\u6210\u529f"
}
```

4.示例
```js
$.post('/event/sort', {
  ids: ids,
  eid: eid
});
```
