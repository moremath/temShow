###添加或新建
```
url: /rest_api/mt_shop_cart/
method: POST
Content-type: application/json
params:
        登录凭证    
        //Request Body           
        {
            //增加的数量(正整数)
            "nums": int ,　
            "distributor_product_id": int
        }
response:
    // returns: 201
    {
        //总数
        "nums": int, 
        "distributor_product_id": int
    }
    
    //return 403
    {

    "detail": "身份认证信息未提供。"

    }
    
    //return 400   
    {
        // 比如nums为负数或0
        "nums": [ "请填写正确的商品数量" ] 
    }
```
###删除
```
url: /rest_api/mt_shop_cart/{distributor_product_id}/
method: DELETE
params:
    登录凭证
response: 
    //return 204 (成功删除返回空)
    undefined

    //return 403
    {    
        "detail": "身份认证信息未提供。"    
    }

    //return 404
    {    
        "detail": "未找到。"    
    }
```



###重置 
```
url: /rest_api/mt_shop_cart/{distributor_product_id}/ 
[comment]: PATCH是partial_update
method: PUT(PATCH)
Content-type: application/json
params: 
    登录凭证
    //Request Body
    {
        //重置的数量,正整数
        "nums": int,
        "distributor_product_id": int
    }
response:
    //return 200
    {
        "nums": int,
        "distributor_product_id":int
    }
    
    //return 400
    {    
        "nums": [
            "请填写正确的商品数量"
        ]    
    }
        
    //return 404
    {    
        "detail": "未找到。"    
    }
```


###查询

```
url: /rest_api/mt_shop_cart/{distributor_product_id}/ 
method: GET
params:
    登录凭证
response:
    //return 200
    {    
        "nums": int,
        "distributor_product_id": int    
    }

    //return 404
    {　
        "detail": "未找到。"　
    }

    //return 403
    {　
        "detail": "身份认证信息未提供。"　
    }        


url: /rest_api/mt_shop_cart/?page={page}
method: GET
params:
    登录凭证
    page=int
response:
    //return 200
    [
        {
            "nums": int,
            "distributor_product_id": int,
            "product_detail": {
                "title": "红牛",
                "price": 5.0,
                "id": 12,
                "is_sell": 1,
                "image": "http://ttyx.qunzhu.me/bg.jpg",
                "desc": "1995年12月，“红牛”凭着......打开中国市场，逐步发展成为中国饮料行业的领军品牌。"
            }
        },
        
        ......
    ]
    // return 403
    { 
        "detail": "身份认证信息未提供。" 
    }
```


