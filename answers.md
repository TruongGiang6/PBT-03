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

## Câu A4:
1. Tính specificity score(a, b, c):
- rule A: (0, 0, 1)
- rule B: (0, 1, 0)
- rule C: (1, 0, 0)
- rule D: (0, 1, 1)
2. Element sẽ có màu đỏ vì rule C là rule duy nhất chứa ID selector nên sẽ có độ ưu tiên cao nhất trong 4 rule
3. Nếu thêm <p class="price" id="main-price" style="color: orange;">, element sẽ có màu cam vì inline CSS có độ ưu tiên cao nhất, mạnh hơn tất cả các selector thường
4. Nếu Rule A thêm !important, element sẽ có màu đen vì từ khóa !important có quyền lực tuyệt đối, nó vô hiệu hóa mọi quy tắc tính điểm specificity và ghi đè cả inline CSS

## PHẦN B:

## Câu B1:

** Các loại selector đã sử dụng:
1. Element selector: body, header, table, footer
2. Class selector: .active
3. Descendant selector: nav a
4. Pseudo-class selector: a:hover, tr:nth-child(even)
, tr:hover
5. Universal selector: *

## Câu B2:

- Hộp 1 (content-box): chiều rộng thực tế = 350px  
- Hộp 2 (border-box): chiều rộng thực tế = 300px  

** Giải thích
- Với content-box: width chỉ tính phần content
-> Tổng chiều rộng = content (300px) + padding (40px) + border (10px)
-> 300 + 40 + 10 = 350px

- Với border-box: width đã bao gồm content + padding + border
-> Tổng chiều rộng vẫn là 300px

## Câu B3:

1. Danh sách các rule:
- p -> (0,0,1)
- .text -> (0,1,0)
- .highlight -> (0,1,0)
- p[class] -> (0,1,1)
- body p -> (0,0,2)
- .text.highlight -> (0,2,0)
- #demo -> (1,0,0)
- #demo.text -> (1,1,0)
- #demo.text.highlight -> (1,2,0)
- .force (!important) -> override tất cả

2. Element cuối cùng hiển thị màu teal vì CSS chọn rule có specificity cao nhất
 
3. ![alt text](PBT3_B3.png)

4. Nếu thay đổi thứ tự rules trong CSS file kết quả không đổi vì CSS không ưu iên vị trí khi specificity khác nhau và chỉ khi specificity bằng nhau mới xét thứ tự

## PHẦN C:

## Câu C1:

1. - Chiều rộng thực tế của sidebar:
    + width = 300px
    + padding = 20px (2 bên = 40px)
    + border = 1px (2 bên = 2px)
    -> Tổng = 300 + 40 + 2 = 342px
   - Chiều rộng thực tế của content (content-box!): 
    + width = 660px
    + padding = 30px (2 bên = 60px)
    + border = 1px (2 bên = 2px)
    -> Tổng = 660 + 60 + 2 = 722px

2. Layout bị vỡ vì container là 960px mà tổng chiều rộng của sidebar và content là 1064px nên không còn đủ khoảng trống trên cùng một hàng, khiến khối content bị đẩy xuống dòng tiếp theo

## Câu C2:

1. "Sản phẩm A" (h2)
- font-size = 20px vì rule .card .title nhắm trực tiếp vào thẻ h2 này. Trong CSS, các thuộc tính được xác định trực tiếp sẽ luôn thắng các thuộc tính được kế thừa từ cha (như body hay .container)
- color = green vì có 3 rule cùng tác động đến màu sắc của thẻ này: .card (blue), #featured .title (red), và .highlight (green !important). Mặc dù ID selector (#featured .title) có độ ưu tiên cao hơn class, nhưng từ khóa !important trong rule .highlight là mức ưu tiên cao nhất, do đó màu xanh lá cây được áp dụng

2. "Mô tả sản phẩm" (p trong card featured)
-color = blue vì thẻ p này có thuộc tính color: inherit. Thuộc tính này ép thẻ p phải lấy giá trị màu từ phần tử cha trực tiếp của nó là .card thay vì lấy từ body. Vì .card có màu xanh da trời (blue), nên thẻ p này hiển thị màu xanh da trời

3. "Sản phẩm B" (h2)
-font-size = 20px vì tương tự Sản phẩm A, rule .card .title nhắm trực tiếp vào phần tử này với độ ưu tiên cao hơn các giá trị kế thừa.
-color = blue vì rule #featured .title không áp dụng cho thẻ này vì nó không nằm trong ID featured. Rule .highlight cũng không có trên thẻ này. Do đó, nó kế thừa màu sắc từ phần tử cha trực tiếp là .card

4. "Mô tả sản phẩm B" (p.highlight)
-color = green: mặc dù thẻ p trong .card thường nhận thuộc tính color: inherit (màu xanh), nhưng thẻ này có class .highlight. Quy tắc Cascade quy định rằng một selector trực tiếp (.highlight) sẽ ghi đè thuộc tính được kế thừa. Đặc biệt, với sự xuất hiện của !important, màu xanh lá cây (green) sẽ chiếm ưu thế tuyệt đối