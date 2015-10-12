#查看专场
- [品牌/标题数据](#品牌/标题数据)
- [商品图数据](#商品图数据)
- [表格插件数据](#表格插件数据)
- [表格插件](#表格插件)
#品牌/标题数据
```js
 <input type="hidden" id="event_id" value="{{$event['id']}}">
 {{$event['brand']['name']}} //专场品牌
 {{$event['title']}} //专场标题
```
#商品图数据
```js
//例：
 <div class="fl"  bind-fileupload='{"type":"image", "maxsize" : 2000}'>
    <img src="{{$event['image_pc_small']['image_path']}}" width="100" height="100" alt="" />
  </div>
  
  //PC 专场图：（322*308）
  bind-fileupload='{"type":"image", "maxsize" : 2000}'
  src="{{$event['image_pc_small']['image_path']}}"
  
  //PC Banner：（1920*250）
  bind-fileupload='{"type":"image", "maxsize" : 2000}'
  src="{{$event['image_pc_banner']['image_path']}}"
  
  //App 专场图：（1080*462）
  bind-fileupload='{"type":"image", "maxsize" : 2000}'
  src="{{$event['image_app_big']['image_path']}}"
  
  //App 专场图：（770*540）
  bind-fileupload='{"type":"image", "maxsize" : 2000}' 
  src="{{$event['image_app_small']['image_path']}}"
  
  //App Banner图：（770*540）
  bind-fileupload='{"type":"image", "maxsize" : 2000}'
  src="{{$event['image_app_banner']['image_path']}}"
```
#表格插件数据
```js
<%= id %> //商品ID
<%= title %> //商品信息
<%= sales_price %><%= market_price %> //价格（元）
<%= stock %> //库存
<%= commission %> //佣金
<%= begin_at %>/<%= end_at %> //开始/结束时间
<%= status_name %> //状态
```

#表格插件
```js
	var table = $('#datatable').dataTable({
		url: '/event/eventitems?event_id=' + $('#event_id').val(),
		param: {
			page_size: 3 //每页显示多少条数据
		}
	});
```
