#新增专场

#form表单参数
```js
enctype='multipart/form-data',

method="post"

<input type="hidden" name="event_id" value="{{$event['id']}}">

```
#验证上传图片
```js
<div class="bind-fileupload fl"  bind-fileupload='{"type":"image", "maxsize" : 2000,  "width": 322, "height" : 308}'>
 bind-fileupload='{"type":"image", "maxsize" : 2000,  "width": 322, "height" : 308}'
 //类型：图片，最大容量：2000，宽度：322，高度：308
```
#上传图片数据
```js
//PC 专场图：（322x308）
bind-fileupload='{"type":"image", "maxsize" : 2000,  "width": 322, "height" : 308}'
data-bitmap="/img/imgsize/322_308.gif" //默认图片
data-img="{{$event['image_pc_small']['image_path']}}" //绑定上传图片路径
value="{{$event['image_pc_small']['id']}}" 

//PC Banner：（1920x250）
bind-fileupload='{"type":"image", "maxsize" : 2000,  "width": 1920, "height" : 250}'
data-bitmap="/img/imgsize/1920_250.gif"
data-img="{{$event['image_pc_banner']['image_path']}}"
value="{{$event['image_pc_banner']['id']}}"

//App 专场图：（1080x462）
bind-fileupload='{"type":"image", "maxsize" : 2000,  "width": 1080, "height" : 462}'
data-bitmap="/img/imgsize/1080_462.gif" 
data-img="{{$event['image_app_big']['image_path']}}"
value="{{$event['image_app_big']['id']}}"

//App 专场图：（770x540）
bind-fileupload='{"type":"image", "maxsize" : 2000,  "width": 770, "height" : 540}'
data-bitmap="/img/imgsize/770_540.gif" 
data-img="{{$event['image_app_small']['image_path']}}"
value="{{$event['image_app_small']['id']}}"

//App Banner图：（720x290）
bind-fileupload='{"type":"image", "maxsize" : 2000,  "width": 720, "height" : 290}'
data-bitmap="/img/imgsize/720_290.gif" 
data-img="{{$event['image_app_banner']['image_path']}}"
value="{{$event['image_app_banner']['id']}}"
```
//数据提交验证
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
