#删除专场

1.请求地址
```js
/event/delete
```
2.请求参数
```js
{
 event_id: id //商品id
 }
```
3.返回结果
```js
{
 event_id：135
}
```
4.示例
```js
$(".event_del").on('click', function () {
		if (confirm('确定要删除吗')) {
			var id = $(this).data('id');
			$.post('/event/delete', {
				event_id: id
			}, function (res) {
				if (res.errorcode === 0) {
					location.reload();
				}
			});
		}
		return false;
	})
```
