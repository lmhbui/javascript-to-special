#商品排序
- [商品数据](#商品数据)
- [排序功能](#排序功能)

#商品数据
```js
<span class="b18">{{$event['brand']['name']}} - 商品排序</span>
<input type="hidden" id="eid" value="{{$_GET['event_id']}}">
  <ul class="event-sort" id="sortable">
    <li id="{{$item['item_id']}}"><p class="goods-id">ID:{{$item['item_id']}}</p>
      <img src="{{$item['item_detail']['image1']['image_path']}}" class="fl mr10" width="150" height="150">
      <p class="goods-tit">{{$item['item_detail']['title']}}</p>
    </li>
  </ul>
```
#排序功能
1.请求地址
```
/event/sort
```
2.请求参数
```js
{
  ids: ids, //商品ids
  eid: eid //专场id
}
```
3.返回结果
```
{
}
```

4.示例
```js
$.post('/event/sort', {
  ids: ids,
  eid: eid
});
```
