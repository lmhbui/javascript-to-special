#查看专场
1.请求地址
```js
  /event/eventitems?event_id=' + $('#event_id').val()
```
2.请求参数
```js
{
	event_id:99,
	ajax:1
	page:1
	page_size:2
}
```
3.返回结果
```js
{
	"errorcode": 0,
	"datatable": {
		"list": [{
			"id": 20000232,
			"title": "113123123452fadsfa",
			"sales_title": "11112331",
			"market_price": "11.00",
			"sales_price": "11.00",
			"supply_price": "9.79",
			"taobao_seller_id": 0,
			"is_buy_change": 0,
			"postage_tpl_id": 0,
			"source_platform": "",
			"source_id": "0",
			"click_url": "",
			"intended_population": "771",
			"stock": 1,
			"status": 1,
			"is_able_apply": 0,
			"create_at": "1437371707",
			"update_at": "1437372078",
			"delete_at": 0,
			"brand_id": 16,
			"cate1_id": 341,
			"cate2_id": 347,
			"cate3_id": 0,
			"partner_id": 17,
			"item_type_id": 1,
			"is_overseas": 0,
			"image_id1": 80,
			"image_id2": 0,
			"website": "",
			"item_official": {
				"id": 20000039,
				"item_id": 20000232,
				"begin_at": 1435680000,
				"end_at": 0,
				"fav_num": 0,
				"not_fav_num": 0,
				"sold_num": 0,
				"read_num": 0,
				"user_buy_min": 1,
				"user_buy_max": 0,
				"user_buy_tuple": 0,
				"is_check": 0,
				"is_recommend": 0,
				"is_boutique": 0,
				"is_wap_boutique": 0,
				"is_tuijian": 0,
				"channel_sign": "",
				"is_auto_delay": 1,
				"sort_num": 0,
				"new_goods_sort_num": 0,
				"nine_goods_sort_num": 0,
				"brand_goods_sort_num": 0,
				"temai_sort_num": 0,
				"maizhe_new_goods_sort_num": 0,
				"maizhe_nine_goods_sort_num": 0,
				"app_new_goods_sort_num": 0,
				"app_nine_goods_sort_num": 0,
				"app_brand_goods_sort_num": 0,
				"app_temai_sort_num": 0,
				"create_at": "0",
				"update_at": "0",
				"delete_at": 0,
				"is_overseas": 1,
				"website": ""
			},
			"begin_at": "2015-07-01",
			"end_at": "----",
			"status_name": "\u5df2\u4e0a\u7ebf",
			"commission": 11
		}, {
			"id": 20000233,
			"title": "fsadfasfasfasdf",
			"sales_title": "21313131",
			"market_price": "2131.00",
			"sales_price": "12.00",
			"supply_price": "10.68",
			"taobao_seller_id": 0,
			"is_buy_change": 0,
			"postage_tpl_id": 0,
			"source_platform": "",
			"source_id": "0",
			"click_url": "",
			"intended_population": "771",
			"stock": 0,
			"status": 1,
			"is_able_apply": 0,
			"create_at": "1437371827",
			"update_at": "1437372062",
			"delete_at": 0,
			"brand_id": 16,
			"cate1_id": 171,
			"cate2_id": 181,
			"cate3_id": 0,
			"partner_id": 17,
			"item_type_id": 1,
			"is_overseas": 0,
			"image_id1": 80,
			"image_id2": 0,
			"website": "",
			"item_official": {
				"id": 20000037,
				"item_id": 20000233,
				"begin_at": 1435680000,
				"end_at": 1437484005,
				"fav_num": 0,
				"not_fav_num": 0,
				"sold_num": 0,
				"read_num": 0,
				"user_buy_min": 1,
				"user_buy_max": 0,
				"user_buy_tuple": 0,
				"is_check": 0,
				"is_recommend": 0,
				"is_boutique": 0,
				"is_wap_boutique": 0,
				"is_tuijian": 0,
				"channel_sign": "",
				"is_auto_delay": 1,
				"sort_num": 0,
				"new_goods_sort_num": 0,
				"nine_goods_sort_num": 0,
				"brand_goods_sort_num": 0,
				"temai_sort_num": 0,
				"maizhe_new_goods_sort_num": 0,
				"maizhe_nine_goods_sort_num": 0,
				"app_new_goods_sort_num": 0,
				"app_nine_goods_sort_num": 0,
				"app_brand_goods_sort_num": 0,
				"app_temai_sort_num": 0,
				"create_at": "0",
				"update_at": "1437484006",
				"delete_at": 0,
				"is_overseas": 1,
				"website": ""
			},
			"begin_at": "2015-07-01",
			"end_at": "2015-07-21",
			"status_name": "\u5df2\u4e0b\u7ebf",
			"commission": 11
		}],
		"total_count": 3
	}
}
```
4.示例
```js
$(function () {
        var table = $('#datatable').dataTable({
            url: '/event/eventitems?event_id=' + $('#event_id').val(),
            param: {
                page_size: 2 //每页显示多少条数据
            }
        });
    });
```
