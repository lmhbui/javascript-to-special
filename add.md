#新增专场
- [数据提交验证](#数据提交验证)

#数据提交验证
1.地址
```js
/event/add
```
2.参数
```js
{
  "method":"post",
  "enctype":'multipart/form-data'
}
```
3.返回结果
```js
{
  event_id:150,
  &brand_id:28
}
```
4.示例
```js
  var form = $("#form");
  form.Validform({
      callback: function () {
          _post();
          return false;
      }
  });
 function _post() {
      var pram = form.serialize();
      $.post('/event/add', pram, function (res) {
          if (res.errorcode === 0) {
              window.location.href = '/event/items?event_id=' + res.event_id + '&brand_id=' + res.brand_id;
              return false;
          }
      });
  }
```
