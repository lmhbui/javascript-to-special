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
  event_id: eventId, //id
  item_id: ids, //商品id
  item_status: status //审核状态
}
```
3.返回结果
```js
{
event_id:99
item_id:20000232,20000233,20000278,20000279
item_status:1
 }
```
4.示例
```js
//批量提交数据
$.post('/event/muloperate', {
    event_id: eventId,
    item_id: ids,
    item_status: status
}, function (res) {
    if (!res.error) {
        reShow(ids, status);
    }
});
```

