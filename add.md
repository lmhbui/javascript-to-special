#新增专场

1.请求地址
```js
/event/add
```
2.请求参数
```js
{
brand_id:16，
title:4234234，
image_pc_small_id:50，
image_pc_banner_id:50，
image_app_big_id:50，
image_app_small_id:50，
image_app_banner_id:50，
event_id:99
}
```
3.返回结果
```js
{
	"errorcode": 1,
	"message": "\u4e13\u573a\u4fdd\u5b58\u5931\u8d25"
}
```
4.示例
```js
    var pram = form.serialize();
    $.post('/event/add', pram, function (res) {
        if (res.errorcode === 0) {
            window.location.href = '/event/items?event_id=' + res.event_id + '&brand_id=' + res.brand_id;
            return false;
        }
    });
```
