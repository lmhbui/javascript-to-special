#提交审核
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
