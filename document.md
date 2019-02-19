# Document BBH SDK

### Thiết lập
- Truy cập botbanhang.vn/page để đăng nhập
- Chọn page
- Chọn Web Application 
- Tạo ứng dụng
- Kích hoạt
- Trong ứng dụng vừa tạo sẽ có mã nhúng dạng
```
<script src="https://media.botbanhang.vn/libs/api.min.js"></script>
<script>
  var BotBanHang = BotBanHang.init({
    app_id: "225739c0-339b-11e9-9b37-637e136097a8",
    version: "v1.3"
  })
</script>
```
- Nhúng trực tiếp vào tag head trong html
- Các mã SDK được nhúng trực tiếp vào tag `script` để sử dụng
## SDK DOCUMENT

### 1. CATEGORY
- Truy vấn toàn bộ thông tin danh mục, bao gồm danh mục cha và các danh mục con
```
BotBanHang.category.getCategory()
```
- Response Example:
```
{
  "data": [
    {
      "subCategories": [ // Danh sách danh mục con
        {
          "page": "5c0729df6f92d42919aff017", // ID của page trong Bot Bán Hàng
          "status": 1,
          "title": "ao khoac", // Tiêu đề danh mục
          "level": 2,
          "parent": "5c6adf2481bdebfa1c411fa2", // ID danh mục cha của nó
          "image_url": "https://media.botbanhang.vn/uploads/5c0729df6f92d42919aff017/8585e2d6-24f5-404d-981d-5ddf77bff06f.png",
          "isSubCategory": true,
          "subtitle": "êfefefef", // Phụ đề
          "discount": 0,
          "index": 1,
          "price": 1000,
          "symbol": "đ",
          "quantity": 0,
          "stock": 100,
          "description": "",
          "weight": 0,
          "images_url": [
            "https://media.botbanhang.vn/no-image.png"
          ],
          "product_type": "product",
          "can_order_oversell": false,
          "is_private": false,
          "uuid": "7f64f120-339b-11e9-99a7-8f2b23277d23",
          "createdAt": "2019-02-18T16:37:36.178Z",
          "updatedAt": "2019-02-18T16:37:36.178Z",
          "id": "5c6adf5051fc690848bd09da" // ID của danh mục
        },
        {
          // Danh mục tiếp theo
        }
      ],
      "page": "5c0729df6f92d42919aff017", // ID của page trong Bot Bán Hàng
      "status": 1,
      "title": "quan ao", // Tiêu đề của danh mục
      "level": 1,
      "image_url": "https://media.botbanhang.vn/uploads/5c0729df6f92d42919aff017/9fe73cab-644a-4c5e-ab9f-2a8092ff4281.jpg",
      "isSubCategory": false,
      "subtitle": "ádfasdfasdfasdfasdf", // Phụ đề
      "payload": "<CAT_QUAN_AO",
      "discount": 0,
      "index": 1,
      "price": 1000,
      "symbol": "đ",
      "quantity": 0,
      "stock": 100,
      "description": "",
      "weight": 0,
      "images_url": [
        "https://media.botbanhang.vn/no-image.png"
      ],
      "product_type": "product",
      "can_order_oversell": false,
      "is_private": false,
      "uuid": "65976980-339b-11e9-bb32-f133572bbba8",
      "createdAt": "2019-02-18T16:36:52.888Z",
      "updatedAt": "2019-02-18T16:36:52.888Z",
      "id": "5c6adf2481bdebfa1c411fa2" // ID của danh mục
    },
    {
      // Danh mục tiếp theo
    }
  ]
}
```

### 2. PRODUCT 
- Truy vấn toàn bộ danh sách sản phẩm
```
BotBanHang.category.getProduct({})
```
- Response Example:
```
{
  "data": [
    {
      "page": "5c0729df6f92d42919aff017", // ID của page trong BOT BÁN HÀNG
      "parent": "5c6adf5051fc690848bd09da", // ID của danh mục chứa sản phẩm
      "status": 1,
      "title": "áo khoac nam thoi trang", // Tiêu đề
      "level": 3,
      "price": 0,
      "images_url": [
        "https://media.botbanhang.vn/uploads/5c0729df6f92d42919aff017/9aa977db-382f-48a5-8869-ca3861e5946a.png"
      ],
      "discount": 0,
      "product_type": "product",
      "stock": 100,
      "index": 1,
      "subtitle": "",
      "symbol": "đ",
      "quantity": 0,
      "description": "",
      "weight": 0,
      "image_url": "https://media.botbanhang.vn/no-image.png",
      "can_order_oversell": false,
      "is_private": false,
      "uuid": "79805a50-3400-11e9-80fd-3bfe4be0b045",
      "createdAt": "2019-02-19T04:40:25.461Z",
      "updatedAt": "2019-02-19T04:40:25.461Z",
      "id": "5c6b88b9445a21e70e4eeb1d" // ID của sản phẩm
    },
    {
      // Sản phẩm tiếp theo
    }
  ]
}
```
- Truy vấn tìm kiếm một sản phẩm dựa trên `ID`
```
BotBanHang.category.getProduct({id: "id_san_pham"})
```
- Request Example:
```
BotBanHang.category.getProduct({id: "5c6b8909c1e29de60e15f72f"})
```
- Response Example:
```
{
  "data": [
    {
      "page": "5c0729df6f92d42919aff017", // ID của page trong BOT BÁN HÀNG
      "parent": "5c6adf5051fc690848bd09da", // ID của danh mục
      "status": 1,
      "title": "ao nam sau", // Tiêu đề
      "level": 3,
      "price": 0,
      "images_url": [
        "https://media.botbanhang.vn/uploads/5c0729df6f92d42919aff017/c59983d4-e3c0-409f-802e-ca0c183523e5.png"
      ],
      "discount": 0,
      "product_type": "product",
      "stock": 100,
      "index": 1,
      "subtitle": "",
      "symbol": "đ",
      "quantity": 0,
      "description": "",
      "weight": 0,
      "image_url": "https://media.botbanhang.vn/no-image.png",
      "can_order_oversell": false,
      "is_private": false,
      "uuid": "a9160df0-3400-11e9-babb-d9c2c8af0c7a",
      "createdAt": "2019-02-19T04:41:45.295Z",
      "updatedAt": "2019-02-19T04:41:45.295Z",
      "id": "5c6b8909c1e29de60e15f72f" // ID sản phẩm
    }
  ]
}
```
- Truy vấn danh sách sản phẩm theo danh mục, có tìm kiếm và phân trang
```
BotBanHang.category.getListProduct({
      parent: "id_danh_muc", 
      limit: "gioi_han_ban_ghi", // number
      skip: "phan_trang", // number
      search: "tim_kiem" // string
    })
```
- Request Example:
```
BotBanHang.category.getListProduct({
      parent: "5c6adf5051fc690848bd09da",
      limit: "20",
      skip: "0",
      search: "trang"
    })
```
- Response Example:
```
{
  "data": [
    {
      "page": "5c0729df6f92d42919aff017",
      "parent": "5c6adf5051fc690848bd09da",
      "status": 1,
      "title": "áo khoac nam thoi trang",
      "level": 3,
      "price": 0,
      "images_url": [
        "https://media.botbanhang.vn/uploads/5c0729df6f92d42919aff017/9aa977db-382f-48a5-8869-ca3861e5946a.png"
      ],
      "discount": 0,
      "product_type": "product",
      "stock": 100,
      "index": 1,
      "subtitle": "",
      "symbol": "đ",
      "quantity": 0,
      "description": "",
      "weight": 0,
      "image_url": "https://media.botbanhang.vn/no-image.png",
      "can_order_oversell": false,
      "is_private": false,
      "uuid": "79805a50-3400-11e9-80fd-3bfe4be0b045",
      "createdAt": "2019-02-19T04:40:25.461Z",
      "updatedAt": "2019-02-19T04:40:25.461Z",
      "id": "5c6b88b9445a21e70e4eeb1d"
    }
  ]
}
```
### 3. ME
- Truy vấn thông tin người đang truy cập
```
BotBanHang.user.me()
```
- Response Example:
```
{
  "data": {
    "id": "5c072e5fe503e8855fd52e47", // ID của người truy cập
    "first_name": "TriÂn",
    "last_name": "HộpThư",
    "name": "TriÂn HộpThư",
    "gender": "male",
    "avatar": "/avatar/2874888275870129",
    "email": null
  }
}
```
### 4. CONTACTS
- Truy vấn thông tin liên hệ của người đang truy cập
```
BotBanHang.user.getContacts()
```
- Response Example:
```
{
  "data": [
    {
      "client": "5c072e5fe503e8855fd52e47", // ID của người truy cập
      "name": "TriÂn HộpThư",
      "tel": "0333776915",
      "address": "dd,ddd,ddd", 
      "province": "64", // Mã tỉnh
      "district": "638", // Mã huyện
      "email": null,
      "createdAt": "2019-02-19T07:25:37.502Z",
      "updatedAt": "2019-02-19T07:25:37.502Z",
      "id": "5c6baf716b255bae66a88bc1" // ID riêng của địa chỉ
    },
    {
      // Thông tin địa chỉ tiếp theo
    }
  ]
}
```
- Thêm thông tin liên hệ của người đang truy cập
```
BotBanHang.user.addContact({
  name: "ten",
  email:"dia_chi_mail",
  tel:"so_dien_thoai", 
  address:"dia_chi", 
  province:"ma_tinh", 
  district:"ma_huyen"
  })
```
- Request Example:
```
BotBanHang.user.addContact({
      name: "Minh Thien",
      email: "adfd@gmail.com",
      tel: "03887464",
      address: "dfdf,dfdf,dfdfd",
      province: "64",
      district: "638"
    })
```    
- Response Example:
```
{
  "data": [
    {
      "client": "5c072e5fe503e8855fd52e47", // ID của người truy cập
      "name": "Minh Thien",
      "tel": "03887464",
      "address": "dfdf,dfdf,dfdfd", 
      "province": "64", // Mã tỉnh
      "district": "638", // Mã huyện
      "email": nuadfd@gmail.comll,
      "createdAt": "2019-02-19T07:25:37.502Z",
      "updatedAt": "2019-02-19T07:25:37.502Z",
      "id": "5c6baf716b255bae66a88er4" // ID riêng của địa chỉ
    }
  ]
}
```
- Xóa thông tin liên hệ của người đang truy cập
```
BotBanHang.user.removeContact(id: "id riêng của địa chỉ")
```
- Request Example:
```
BotBanHang.user.removeContact("5c6bb4996b255bae66a88e61")
```
- Response Example:
```
{
  "data": [
    {
      "client": "5c072e5fe503e8855fd52e47",
      "name": "Minh Thien",
      "email": "adfd@gmail.com",
      "tel": "03887464",
      "address": "dfdf,dfdf,dfdfd",
      "province": "64",
      "district": "638",
      "createdAt": "2019-02-19T07:47:37.679Z",
      "updatedAt": "2019-02-19T07:47:37.679Z",
      "id": "5c6bb4996b255bae66a88e61"
    }
  ]
}
```
### 5. FLOW
- Gửi một kịch bản cho người đang truy cập
```
BotBanHang.user.activeFlow({flow: "id_cua_kich_ban"})
```
- Request Example:
```
BotBanHang.user.activeFlow({flow: "5c072d9ee503e8855fd52c2c"})
```
- Response Example:
```
{"data":{"success":true}}
```
### 6. PROVINCE
- Truy vấn danh sách mã tỉnh
```
BotBanHang.geo.getProvince()
```
- Response Example:
```
{
  "data": [
    {
      "name": "Lào Cai",
      "slug": "lao-cai",
      "type": "tinh",
      "name_with_type": "Tỉnh Lào Cai",
      "code": "10"
    },
    {
      "name": "Điện Biên",
      "slug": "dien-bien",
      "type": "tinh",
      "name_with_type": "Tỉnh Điện Biên",
      "code": "11"
    },
    {
      // tỉnh tiếp theo
    }
  ]
}
```
### 7. DISTRICT
- Truy vấn danh sách mã thành phố dựa trên mã tỉnh
```
BotBanHang.geo.getDistrict(ma_tinh)
```
- Request Example:
```
BotBanHang.geo.getDistrict(10)
```
- Response Example:
```
{
  "data": [
    {
      "name": "Lào Cai",
      "type": "thanh-pho",
      "slug": "lao-cai",
      "name_with_type": "Thành phố Lào Cai",
      "path": "Lào Cai, Lào Cai",
      "path_with_type": "Thành phố Lào Cai, Tỉnh Lào Cai",
      "code": "080",
      "parent_code": "10"
    },
    {
      "name": "Bát Xát",
      "type": "huyen",
      "slug": "bat-xat",
      "name_with_type": "Huyện Bát Xát",
      "path": "Bát Xát, Lào Cai",
      "path_with_type": "Huyện Bát Xát, Tỉnh Lào Cai",
      "code": "082",
      "parent_code": "10"
    },
    {
      // thành phố tiếp theo
    }
  ]
}
```
### 8. PAGE
- Truy vấn thông tin page
```
BotBanHang.page.getPage()
```
- Response Example:
```
{
  "data": {
    "id": "5c0729df6f92d42919aff017",
    "pageid": "2204445623215564",
    "name": "Thời trang - Botbanhang",
    "say_hello": "",
    "cost_free_ship": 100000,
    "display_detail_product": true,
    "isFreeShip": false,
    "feeShip": 20000,
    "textFreeShip": "Miễn phí giao hàng với đơn hàng trên 100.000đ trong nội thành.",
    "syntax_start_bot": "bot",
    "active_contact": false,
    "active_search_product": true,
    "enable_ship_for_page": false,
    "active_direct_inbox": true,
    "active_sms_verify": true,
    "isMaintain": false,
    "isBlock": false,
    "status": 1,
    "label_status": "Chưa thanh toán",
    "text_buy_product": "Mua sản phẩm",
    "text_order": "Đặt hàng",
    "text_please_order": "Vui lòng đặt hàng !",
    "text_confirm_order_ship": "XÁC NHẬN và GIAO HÀNG",
    "text_address_ship": "Địa chỉ nhận hàng",
    "text_mobile_ship": "Số điện thoại nhận hàng",
    "text_note_ship": "Ghi chú khi nhận hàng",
    "text_complete_ship": "HOÀN TẤT GIAO HÀNG!",
    "text_title_ship": "GIAO HÀNG",
    "text_reply_comment_auto": "",
    "text_direct_inbox_auto": "",
    "active_auto_like": true,
    "active_auto_reply": true,
    "active_hide_phone_number": true,
    "text_category__back": "Quay lại",
    "text_category__sort": "Sắp xếp",
    "text_category__sort_new": "Mới nhất",
    "text_category__sort_price_asc": "Giá tăng dần",
    "text_category__sort_price_desc": "Giá giảm dần",
    "text_product__buy_now": "Mua ngay",
    "text_product__category_name": "Danh mục",
    "text_product__label_product": "Sản phẩm",
    "text_product__buy_product": "Mua sản phẩm",
    "text_product__view_product_saved": "Xem sản phẩm đã lưu",
    "text_product__description": "Mô tả sản phẩm",
    "text_cart__your_cart": "giỏ hàng của bạn",
    "text_cart__order": "Đặt hàng",
    "text_delivery__customer_name": "Tên người nhận hàng",
    "text_delivery__customer_phone": "Số điện thoại nhận hàng",
    "text_delivery__customer_address": "Địa chỉ nhận hàng",
    "text_delivery__customer_city": "Thành phố/tỉnh",
    "text_delivery__customer_dist": "Quận/huyện",
    "text_delivery__customer_note": "Ghi chú khi nhận hàng",
    "text_delivery__pick_payment": "Chọn hình thức thanh toán",
    "version": "1.2",
    "activeShip3rd": false,
    "contacts": [],
    "active_chat": false,
    "default_product_type": "product",
    "enable_collect_email": false,
    "enable_tax": false,
    "enable_promotion": false,
    "hide_out_stock": false,
    "enable_payment": false,
    "default_pause": 10,
    "hide_select_payment": false,
    "isEnterprise": true,
    "enable_inventory": false
  }
}
```
### 9. CART
- Truy vấn các sản phẩm trong giỏ hàng
```
BotBanHang.order.getCart()
```
- Response Example:
```
{
  "data": {
    "id": "5c6bb2216b255bae66a88d29",
    "createdAt": "2019-02-19T07:37:05.782Z",
    "idorder": 1273522,
    "updatedAt": "2019-02-19T07:37:12.860Z",
    "orders": [
      {
        "id": "5c6baf2b6b255bae66a88ba2",
        "title": "ao",
        "price": 1000,
        "discount": 999,
        "images_url": [
          "https://media.botbanhang.vn/uploads/5c0729df6f92d42919aff017/0b107770-f196-4a3f-9196-89a68732912d.png"
        ],
        "quantity": 1
      },
      {
        // Sản phẩm tiếp theo
      }
    ],
    "total_price": 999,
    "total_quantity": 1
  }
}
```
- Thêm sản phẩm vào giỏ hàng
```
BotBanHang.order.updateCart({orders})
```
- Request Example:
```
{
  "orders": [
    {
      "page": "5c0729df6f92d42919aff017",
      "parent": "5c6adf681e622d0d48ff15ca",
      "status": 1,
      "title": "ao",
      "level": 3,
      "price": 1000,
      "images_url": [
        "https://media.botbanhang.vn/uploads/5c0729df6f92d42919aff017/0b107770-f196-4a3f-9196-89a68732912d.png"
      ],
      "discount": 999,
      "product_type": "product",
      "stock": 100,
      "index": 1,
      "subtitle": "",
      "symbol": "đ",
      "quantity": 5,
      "description": "",
      "weight": 0,
      "image_url": "https://media.botbanhang.vn/no-image.png",
      "can_order_oversell": false,
      "is_private": false,
      "uuid": "63882630-3417-11e9-bbdd-8b75ba94ef7b",
      "createdAt": "2019-02-19T07:24:27.027Z",
      "updatedAt": "2019-02-19T07:24:27.027Z",
      "id": "5c6baf2b6b255bae66a88ba2",
      "share_content": {
        "attachment": {
          "type": "template",
          "payload": {
            "template_type": "generic",
            "elements": [
              {
                "title": "ao",
                "default_action": {
                  "type": "web_url",
                  "url": "https://botbanhang.vn/app/2204445623215564/products/5c6baf2b6b255bae66a88ba2",
                  "messenger_extensions": true,
                  "webview_height_ratio": "full"
                },
                "image_url": "https://media.botbanhang.vn/uploads/5c0729df6f92d42919aff017/0b107770-f196-4a3f-9196-89a68732912d.png",
                "buttons": [
                  {
                    "title": "Mua sản phẩm",
                    "type": "web_url",
                    "url": "http://m.me/2204445623215564?ref=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJwcm9kdWN0IjoiNWM2YmFmMmI2YjI1NWJhZTY2YTg4YmEyIiwiaWF0IjoxNTUwNTY1MDkyLCJleHAiOjE1NTE0MjkwOTIsImF1ZCI6IjEiLCJpc3MiOiIxIn0.zJGX1Vx4n60kQ_G0a2LsqtnFrMEnzwWUbE9E4KZDRP8"
                  }
                ]
              }
            ]
          }
        }
      },
      "extra_option": {}
    }
  ]
}
```
- Response Example:
```

```
- Đặt hàng
```
BotBanHang.order.checkout({order, contact, name_ship, tel_ship, address_ship, province_ship, district_ship, email, note})
```
- Request Example:
```
{
  "order": {
    "page": "5c0729df6f92d42919aff017",
    "client": "5c072e5fe503e8855fd52e47",
    "userid": "2874888275870129",
    "name_ship": "TriÂn HộpThư",
    "orders": [
      {
        "id": "5c6baf2b6b255bae66a88ba2",
        "title": "ao",
        "price": 1000,
        "discount": 999,
        "images_url": [
          "https://media.botbanhang.vn/uploads/5c0729df6f92d42919aff017/0b107770-f196-4a3f-9196-89a68732912d.png"
        ],
        "quantity": 2
      }
    ],
    "total_price": 1998,
    "total_quantity": 2,
    "status": "pending",
    "is_paid": false,
    "is_reviewed": false,
    "uuid": "27c8d250-3419-11e9-bbdd-8b75ba94ef7b",
    "idorder": 1273522,
    "createdAt": "2019-02-19T07:37:05.782Z",
    "updatedAt": "2019-02-19T08:26:29.678Z",
    "id": "5c6bb2216b255bae66a88d29",
    "contact": "5c6baf716b255bae66a88bc1",
    "tel_ship": "0333776915",
    "address_ship": "dd,ddd,ddd",
    "province_ship": "64",
    "province_name": "Gia Lai",
    "district_ship": "638",
    "district_name": "Phú Thiện",
    "email": null,
    "payment": "",
    "full_address": "dd,ddd,ddd, Phú Thiện, Gia Lai",
    "promotion": null,
    "phone": "+84333776915"
  },
  "type": "confirm"
}
```
- Response Example:
```
```