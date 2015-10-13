#专场列表
- [tab数据统计](#专场列表-tab数据统计)
- [删除操作](#专场列表-删除操作)

#专场列表-tab数据统计

1.请求地址
```js
/event/count
```
2.请求参数
```js
{

}
```
3.返回结果
```js
{
	
}
```
4.示例
```js
setTimeout(function () {
		var i = $('.dc-tab').find('i');
		$.post('/event/count')
			.done(function (res) {
				_.each(res, function (val, index) {
			i.eq(index).text(val);
				});
	});
	}, 10);
```
#专场列表-删除操作

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
