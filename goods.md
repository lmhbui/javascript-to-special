#商品管理
- [tab切换](#tab切换)
- [批量操作功能](#表格-批量操作功能)

#tab切换
1.请求地址
```js
  /event/statuscount
```
2.请求参数
```js
{
 event_id: eid
}
```
3.返回结果
```js
{
  event_id:99
}
```
4.示例
```js
 //Tab数据统计
    setTimeout(function () {
        var i = $('.dc-tab').find('i');
        var eid = $("#event_id").val();
        $.post('/event/statuscount', {
                event_id: eid
            })
            .done(function (res) {
                _.each(res, function (val, index) {
                    i.eq(index).text(val);
                });
            });
    }, 10);
```


#表格-批量操作功能
1.请求地址
```js
{
  /event/muloperate
}
```
2.请求参数
```js
{
event_id:136
item_id:20000249
item_status:1
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
//批量提交数据
$.post('/event/muloperate', {
    event_id: eventId,//专场id
    item_id: ids,//商品id
    item_status: status //审核状态
}, function (res) {
    if (!res.error) {
        reShow(ids, status);
    }
});
```

