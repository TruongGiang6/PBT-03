## PHẦN A:

## Câu A1:

*** Cách 1: Inline CSS ***
- VD: <p style="color: red; font-size: 18px;">Đây là đoạn văn màu đỏ</p>
- Ưu điểm: Nhanh, tiện lợi khi cần test code nhanh
- Nhược điểm: Không tái sử dụng, khó bảo trì (phải sửa từng dòng), làm HTML rối
- Khi nào nên dùng: khi cần test nhanh, ghi đè tạm thời

*** Cách 2: Internal CSS ***
- VD: 
<!DOCTYPE html>
    <html>
        <head>
            <style>
                p {
                    color: blue;
                    font-size: 16px;
                }
            </style>
        </head>
        <body>
            <p>Đây là đoạn văn màu xanh</p>
        </body>
    </html>
- Ưu điểm: không cần tạo thêm file CSS
- Nhược điểm: file HTML dài hơn, không dùng cho site khác
- Khi nào nên dùng: khi web có 1 trang, demo bài tập

*** Cách 3: External CSS ***
- VD: 
+ ở file HTML: 
<link rel="stylesheet" href="style.css">
<p>Đây là đoạn văn</p>

+ ở file CSS:
p {
  color: green;
  font-size: 20px;
}
- Ưu điểm: tái sử dụng nhiều trang, dễ bảo trì, code sạch, tách biệt HTML & CSS
- Nhược điểm: phải quản lý file riêng, sẽ lỗi nếu sai đường dẫn
- Khi nào nên dùng: Web có nhiều site, dùng cho các dự án lớn

- Nếu cùng 1 element có cả 3 cách CSS đồng thời áp dụng, cách Inline "thắng" vì CSS hoạt động theo cơ chế xếp tầng, Style càng gần element thì càng mạnh.

## Câu A2:

1. h1                           → Chọn: ShopTLU
2. .price                       → Chọn: 25.990.000đ và 45.990.000đ
3. #app header                  → Chọn: toàn bộ khối thẻ <header>, bao gồm các text ShopTLU, Home, Products, About
4. nav a:first-child            → Chọn: Home
5. .product.featured h2         → Chọn: MacBook Pro
6. article > p                  → Chọn: 25.990.000đ, Mô tả sản phẩm..., 45.990.000đ, Mô tả sản phẩm...
7. a[href="/"]                  → Chọn: Home
8. .top-bar.dark h1             → Chọn: ShopTLU

## Câu A3:
*** TH1: content-box (mặc định) ***
.box-1 {
    width: 400px;
    padding: 20px;
    border: 5px solid black;
    margin: 10px;
}
→ Chiều rộng hiển thị = 450px
→ Không gian chiếm trên trang = 470px

*** TH2: border-box ***
.box-2 {
    box-sizing: border-box;
    width: 400px;
    padding: 20px;
    border: 5px solid black;
    margin: 10px;
}
→ Chiều rộng hiển thị = 400px
→ Kích thước content thực tế = 350px
→ Không gian chiếm trên trang = 420px

*** TH3: Margin collapse ***
.box-a { margin-bottom: 25px; }
.box-b { margin-top: 40px; }
→ Khoảng cách giữa box-a và box-b = 40px
→ Giải thích tại sao KHÔNG PHẢI 65px? vì CSS có cơ chế margin collapse, trình duyệt sẽ không cộng 2 giá trị mà sẽ lấy giá trị lớn hơn

