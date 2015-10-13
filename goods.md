#商品管理
- [tab切换](#tab切换)
- [提交审核功能](#提交审核功能)
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
  event_id:147
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

#提交审核功能
1.请求地址
```js
/event/audit
```
2.请求参数
```js
{
  event_id: eventId
}

```
3.返回结果
```js
{
  event_id: 124
}
```
4.示例
```js
var eventId = $('#event_id').val()
    $("#event_audit").on('click', function () {
        $.jBox.confirm("提交审核后将不能修改添加商品了，确定要提交吗", "提示", function (v) {
            if (v == "ok") {
                $.post('/event/audit', {
                    event_id: eventId
                }, function (res) {
                    if (res.errorcode === 0) {
                        window.location.href = "/event";
                    }
                });
            }
        });
    });
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
  event_id: 147,
  item_id: 20000014,
  item_status: 待审核
```
4.示例
```js
  //批量操作功能
var eventId = $('#event_id').val(),
   lazyFunc = _.debounce(mulPostFunc, 500, true),
    $(".batch-setting").on('click', function () {
        var ids = check.getSelectIds(),
            type = $(this).data('type');
        lazyFunc(ids, type);
    });
    //批量提交数据
    function mulPostFunc(ids, status) {
        if (ids) {
            $.post('/event/muloperate', {
                event_id: eventId,
                item_id: ids,
                item_status: status
            }, function (res) {
                if (!res.error) {
                    reShow(ids, status);
                }
            });
        }
    }
  //刷新按钮
    function reShow(ids, status) {
        _.each(ids.toString().split(','), function (val) {
            $('.switch[data-id="' + val + '"]')
                .attr('data-is_show', status)
                .removeClass('switch-1')
                .removeClass('switch-0')
                .addClass('switch-' + status);
        });
    }
```

