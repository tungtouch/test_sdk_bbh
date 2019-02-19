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