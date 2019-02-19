# Document BBH @ STUDIO

### Thiết lập
- API Path : `https://api.studio.botbanhang.vn/v1/app/page`
- Mỗi request trong header cần có `token`
  
### Thiết lập truy vấn GET
- Tham số Sort : `{ sort : 'createdAt DESC' }`, `{ sort : 'createdAt ASC' }`
- Tham số Limit : `{ limit : 20 }` , default : 20
- Tham số Skip : `{ skip : 50 }` , default: 0

Ví dụ:
```
[GET] https://api.studio.botbanhang.vn/v1/app/page?id=123&sort=createdAt&skip=10&limit=20
```

## API DOCUMENT 

### 1. PAGES

Truy vấn dữ liệu:
```
[GET] https://api.studio.botbanhang.vn/v1/app/page
```

Thêm dữ liệu:
```
[POST] https://api.studio.botbanhang.vn/v1/app/page
```
- Params: Body data

Sửa dữ liệu:
```
[PUT] https://api.studio.botbanhang.vn/v1/app/page
```
- Params: 
  * Field query : `id`
  * Các field khác để update

- Example:
`[PUT]  https://api.studio.botbanhang.vn/v1/app/page?id=123&name=Tieu-De-Page`

Xoá dữ liệu
```
[DELETE]  https://api.studio.botbanhang.vn/v1/app/page?id=ID_PAGE
```
- Params: 
  * Field query : `id`

### 2. UPLOAD
```
[POST] https://api.studio.botbanhang.vn/v1/app/upload
```
NOTE: Max upload 10MB.

- Body (form-data): 
  * Field: `file` 
  
- Response Example :
```
{
    "data": {
        "file_name": "FILE-1550038722.docx",
        "url": "https://bbh.sgp1.digitaloceanspaces.com/FILE-1550038722.docx",
        "url_cdn": "https://bbh.sgp1.cdn.digitaloceanspaces.com/FILE.docx",
        "file_type": "application/vnd.openxmlformats-officedocument.wordprocessingml.document",
        "file_size": 43251,
        "file_ext": ".docx"
    }
}
```


------

## MODEL   
  
### Page

```
 'user': {
            model: 'users'
            //'id của người tạo/mua template'
        },

        'category': {
            model: 'category'
            // 'ID bảng category',
        },

        'domain': {
            type: 'string'
                // Tên miền của Page
        },
        
        'name': {
            type: 'string'
            // Tiêu đề Page 
        },

        'parent_page': {
            model: 'pages'
            // template referent
        },


        'description': {
            type: 'string'
            // Mô tả
        },

        'source': {
            type: 'string'
            // Source build của Page 
        },

        // backup source khi publish
        'source_publish': {
            type: 'string'
            // Source public của Page
        },

        'thumbnail': {
            type: 'string'
            // url
        },

        'type': {
            type: 'string',
            defaultsTo: '0'
            //'Loại 0 là Page, 1 là Template, 2 là Section',
        },     

        // Trạng thái thanh toán
        'payment_status': {
            type: 'string',
            enum: ['paid', 'pending'], // paid: đã thanh toán , pending: đang chờ
            defaultsTo: 'pending'
        },

        'is_publish': {
            type: 'string',
            defaultsTo: '0'
                //'Đã được public hay vẫn đang trỉnh sửa. 0 - đang trỉnh sửa, 1 - public'
        },

        'deleted': {
            type: 'string',
            defaultsTo: '0'
                // 0: chua xoa, 1: da xoa
        },

        'blocked': {
            type: 'string',
            defaultsTo: '1'
                //'0: Khóa, 1: Hoạt động ',
        },
```