#专场列表
- [链接](#专场列表-链接)
- [数据字段](#专场列表-数据字段)
- [tab数据统计](#专场列表-tab数据统计)
- [删除操作](#专场列表-删除操作)

#专场列表-链接
```js
  //添加专场链接
  <a href="/event/add" class="fr mt5 bui-btn bui-btn-s bui-btn-icon bui-btn-pink"><i class="bui-btn-ico-add"></i>添加专场</a>
  
  //专场列表表格tab切换
  <a href="/event" class="dc-tab {{!isset($_GET['event_status'])?'curr':''}}">全部(<i>-</i>)</a>
  <a href="/event/index?event_status=1" class="dc-tab {{$_GET['event_status']==1?'curr':''}}">待审核(<i>-</i>)</a>
  <a href="/event/index?event_status=2" class="dc-tab {{$_GET['event_status']==2?'curr':''}}">待上线(<i>-</i>)</a>
  <a href="/event/index?event_status=3" class="dc-tab {{$_GET['event_status']==3?'curr':''}}">上线中(<i>-</i>)</a>
  <a href="/event/index?event_status=4" class="dc-tab {{$_GET['event_status']==4?'curr':''}}">已下线(<i>-</i>)</a>
  <a href="/event/index?event_status=5" class="dc-tab {{$_GET['event_status']==5?'curr':''}}">未通过(<i>-</i>)</a>
  <a href="/event/index?event_status=6" class="dc-tab {{$_GET['event_status']==6?'curr':''}}">未提交(<i>-</i>)</a>
  
  //专场列表-操作
  <a class="a-blue" href="/event/add?event_id={{$event['id']}}" >编辑专场</a>
  <a class="a-blue" href="/event/items?event_id={{$event['id']}}&brand_id={{$event['brand_id']}}">商品管理</a>
  <a class="a-blue" href="/event/view?event_id={{$event['id']}}">查看专场</a>
  <a class="a-blue event_del" href="javascript:;" data-id={{$event['id']}}>删除专场</a>
```
#专场列表-数据字段
```js
//专场信息
ID：{{$event['id']}} //商品id
{{$event['title']}}  //商品标题
品牌：{{$event['partner_brand']['title']}} //商品品牌

//在线/总数
0/{{count($event['event_item'])}}

//报名时间
{{date('Y-m-d',$event['create_at'])}}  //返回创建商品时间

//开始/结束时间
  @if($event['begin_at'] && $event['end_at'])
   {{date('Y-m-d',$event['begin_at'])}}至<br/>{{date('Y-m-d',$event['end_at'])}}
  @else
    ---
  @endif

//状态
 {{$event['status_name']}} //返回审核状态名 例：未审核
 
 //操作
 @if($event['status'] < 0)
  <a class="a-blue" href="/event/add?event_id={{$event['id']}}" >编辑专场</a> |
  <a class="a-blue" href="/event/items?event_id={{$event['id']}}&brand_id={{$event['brand_id']}}">商品管理</a>
  <br/>
  <a class="a-blue" href="/event/view?event_id={{$event['id']}}">查看专场</a> |
  <a class="a-blue event_del" href="javascript:;" data-id={{$event['id']}}>删除专场</a>
  @else
    <a href="/event/view?event_id={{$event['id']}}" class="a-blue" >查看专场</a>
  @endif
  
  //分页
  <span>共<em>{{$total_count}}</em>条</span>  //返回数据条数
    @foreach((array)$page_data as $page)
        @if($page['url']) //分页名与对应路径
        <a href="{{$page['url']}}">{{$page['name']}}</a> 
        @else //分页名
        <a class="curr">{{$page['name']}}</a>
        @endif
   @endforeach
  
```
#专场列表-tab数据统计

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
