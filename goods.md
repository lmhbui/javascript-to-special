#商品管理
- [链接](#链接)
- [form表单参数](#form表单参数)
- [tab切换](#tab切换)
- [表格-数据字段](#表格-数据字段)
- [表格-复选框全选功能](#表格-复选框全选功能)
- [提交审核功能](#提交审核功能)
- [批量操作功能](#表格-批量操作功能)
- [是否参加功能](#表格-是否参加功能)

#链接
```js
<a href="/event/sort?event_id={{$event_id}}" class="fr mt5 mr10 bui-btn bui-btn-s bui-btn-icon bui-btn-pink"><i class="bui-btn-ico-add"></i>商品排序</a>
<a href="/event" class="fr mt5 mr10 bui-btn bui-btn-s bui-btn-icon bui-btn-pink"><i class="bui-btn-ico-add"></i>保存</a>
<span class="b18">{{$event['partner_brand']['title']}}专场 - 商品管理</span>&nbsp;&nbsp; <a href="/event/add?event_id={{$event_id}}" class="c-red">修改专场信息>></a>
```
#form表单参数
```js
id="form",
action="/event/items",
  value="{{$input_param['title']}}" //商品名称值
  value="{{$input_param['item_id']}}" //商品id
<input type="hidden" id="event_id" name="event_id" value="{{$event_id}}" />
<input type="hidden" id="brand_id" name="brand_id" value="{{$_GET['brand_id']}}" />
```
#tab切换
```js
<a href="/event/items?event_id={{$event['id']}}&brand_id={{$event['brand_id']}}" class="{{!isset($_GET['item_status'])?'curr':''}} dc-tab">全部(<i></i>)</a>
<a href="/event/items?event_id={{$event['id']}}&brand_id={{$event['brand_id']}}&item_status=1" class="dc-tab {{$_GET['item_status']==1?'curr':''}}">已参加(<i></i>)</a>
<a href="/event/items?event_id={{$event['id']}}&brand_id={{$event['brand_id']}}&item_status=2" class="dc-tab {{$_GET['item_status']==2?'curr':''}}" >未参加(<i></i>)</a>

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
#表格-数据字段
```js
//商品信息
{{$item['image1']['image_path']}} //商品图路径
ID：{{$item['id']}} //商品id
{{$item['title']}} //商品名称

//提报价
{{$item['sales_price']}}

//佣金
{{commission($item['sales_price'],$item['supply_price'])}}

//库存
{{$item['stock']}}

//活动时间
{{ $item['begin_at'] ? date('Y-m-d',$item['begin_at']) : '--'}}至<br/>
{{ $item['end_at'] ? date('Y-m-d',$item['end_at']) : '--'}}

//是否参加
<a href="javascript:;" class="switch switch-{{$item['status']}}" data-id="{{$item['id']}}" data-is_show="{{$item['status']}}">&nbsp;</a>
```
#表格-复选框全选功能
```js
<input type="checkbox" id="select"> //总控制按钮
<input type="checkbox" value="{{$item['id']}}" class="cbx" name="items">

//引入'event/goods/checkbox’ 插件
require(['event/goods/checkbox'], function (Checkbox) {
    var check = new Checkbox({
          allBtn: $('#select'), //总控制按钮
          checkClass: 'cbx'  //复选框中的类名
      });
}
```

#提交审核功能
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
```js
  <input type="button" class="batch-setting mr15 bui-btn bui-btn-m bui-btn-pink" data-type="0" value="批量移除">
  <input type="button" class="batch-setting mr15 bui-btn bui-btn-m bui-btn-pink" data-type="1" value="批量添加">
  
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
#表格-是否参加功能
```js
    //是否参加点击切换
    $('#event_table').on('click', '.switch', function () {
        var my = $(this),
            goodsId = my.data('id'),
            isShow = Number(my.attr('data-is_show'));

        isShow = isShow === 1 ? 0 : 1;
        lazyFunc(goodsId, isShow);
    });
```
