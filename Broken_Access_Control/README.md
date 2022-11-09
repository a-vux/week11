# Lab 1: Unprotected admin functionality
## Lab description:
<p align=center>
    <img src="./src/01_1.png">
</p>

## Solution:
* Truy cập vào robots.txt trên thanh URL, ta thấy một đường dẫn tới mội admin directory
<p align=center>
    <img src="./src/01_2.png">
</p>

* Truy cập vào đường dẫn đó, ta vào được trang admin
<p align=center>
    <img src="./src/01_3.png">
</p>

* Thực hiện xóa user carlos, và lab đã được solved

<br><br>

# Lab 2: Unprotected admin functionality with unpredictable URL
## Lab Description:
<p align=center>
    <img src="./src/02_1.png">
</p>

## Solution:
* Truy cập vào robots.txt trên thanh URL, nhưng không nhận được kết quả gì
<p align=center>
    <img src="./src/02_2.png">
</p>

* F12 check source, thấy được đoạn script sau
<p align=center>
    <img src="./src/02_3.png">
</p>

* Lên URL thử truy cập vào /admin.8ofhgo, ta vào được panel của admin
<p align=center>
    <img src="./src/01_3.png">
</p>

* Xóa user carlos và lab đã được solved

<br><br>

# Lab 3: User role controlled by request parameter
## Lab Description:
<p align=center>
    <img src="./src/03_1.png">
</p>

## Solution:
* Đăng nhập bằng tài khoản của wiener
<p align=center>
    <img src="./src/03_2.png">
</p>

* Bắt request lúc load lại trang, thấy có một cookie tên Admin=false
<p align=center>
    <img src="./src/03_3.png">
</p>

* Sửa giá trị của cookie đó thành true rồi gửi request, ta thấy có thêm một mục nữa là Admin panel
<p align=center>
    <img src="./src/03_4.png">
</p>

* Truy cập vào mục đó, xóa carlos và lab đã được solved

<br><br>

# Lab 4: User role can be modified in user profile
## Lab Description:
<p align=center>
    <img src="./src/04_1.png">
</p>

# Solution: 
* Đăng nhập vào tài khoản wiener, ta thấy trường thay đổi email
<p align=center>
    <img src="./src/04_2.png">
</p>

* Sử dụng email bất kỳ để update, sau đó bắt request gửi sang Repeater. Xem response trả về, thấy được kết quả được trả dưới dạng JSON và email đã được đổi
<p align=center>
    <img src="./src/04_3.png">
</p>

* Đổi roleid sang 2 (lab bảo thế), rồi gửi response
<p align=center>
    <img src="./src/04_4.png">
</p>

* Quay lại trang, thấy đã xuất hiện thêm mục Admin Panel
<p align=center>
    <img src="./src/04_5.png">
</p>

* Vào đó, xóa carlos và lab đã được solved

<br><br>

# Lab 5: URL-based access control can be circumvented
## Lab Description:
<p align=center>
    <img src="./src/05_1.png">
</p>

## Solution:
* Khi vào lab, thấy mục Admin panel, truy cập vào thì thấy bị từ chối. Nhưng đường dẫn chứa tới trang /admin
<p align=center>
    <img src="./src/05_2.png">
</p>

* Bắt request của trang, sử dụng header X-Original-URL với giá trị /admin xuất hiện trên thanh URL
<p align=center>
    <img src="./src/05_3.png">
</p>

* Gửi request thì ta được trang Admin panel, bắt request khi xóa người dùng thấy xuất hiện trang /admin/delete. Và đương nhiên khi forward request này sẽ quay trở lại trang Access denied vì đây là thao tác trên trang của admin, nhưng mình thì bị chặn thao tác trên đó
<p align=center>
    <img src="./src/05_4.png">
</p>

* Quay trở lại trang ban đầu, thay giá trị của X-Original-URL thành /admin/delete, truyền lên bên trên tham số ?username=carlos
<p align=center>
    <img src="./src/05_5.png">
</p>

* Gửi request thì người dùng carlos đã bị xóa, và lab đã được solved

<br><br>

# Lab 6: Method-based access control can be circumvented
## Lab description:
<p align=center>
    <img src="./src/06_1.png">
</p>

## Solution:
* Vào lab, đăng nhập với người dùng administrator, vào Admin panel thấy giao diện sau
<p align=center>
    <img src="./src/06_2.png">
</p>

* Bắt request khi upgrade user carlos, ta nhận được request POST sau
<p align=center>
    <img src="./src/06_3.png">
</p>

* Ném request sang Repeater, rồi log out để log in vào tài khoản của wiener (ko phải admin). Bắt mội request bất kỳ để lấy cookie session, sau đó cop giá trị ném sang cookie ở bên Repeater kia, nhận được kết quả trả về là Unauthorized
<p align=center>
    <img src="./src/06_4.png">
</p>

* Chuột phải vào request rồi chọn Change request method, sửa các giá trị trên tham số thành như sau
<p align=center>
    <img src="./src/06_5.png">
</p>

* Gửi request, và lab đã được solved

<br><br>

# Lab 7: User ID controlled by request parameter
## Lab Description:
<p align=center>
    <img src="./src/07_1.png">
</p>

## Solution:
* Đăng nhập vào tài khoản của wiener, ta thấy được API key của tài khoản cũng như URL xuất hiện param id = wiener
<p align=center>
    <img src="./src/07_2.png">
</p>

* Thay giá trị của id thành carlos, ta nhận được trang tài khoản của carlos
<p align=center>
    <img src="./src/07_3.png">
</p>

* Submit API key cho lab, và lab được solved

<br><br>

# Lab 8: User ID controlled by request parameter, with unpredictable user IDs
## Lab Description:
## Solution:
* Đăng nhập vào tài khoản của wiener, ta thấy được API key của tài khoản cũng như URL xuất hiện param id với giá trị rất ngẫu nhiên
<p align=center>
    <img src="./src/08_2.png">
</p>

* Thử fuzzing quanh app để xem các tài khoản khác, tìm post được đăng tải bởi carlos
<p align=center>
    <img src="./src/08_3.png">
</p>

* Bấm vào link tài khoản carlos, thấy giá trị của id thay đổi. Rất có thể đây là id của carlos
<p align=center>
    <img src="./src/08_4.png">
</p>

* Copy giá trị đó, vào My account rồi paste thay giá trị của mình. Ta nhận được chuyển hướng tới trang của carlos
<p align=center>
    <img src="./src/08_5.png">
</p>

* Submit API key cho lab, và lab được solved

<br><br>

# Lab 9: User ID controlled by request parameter with data leakage in redirect
## Lab Description:
## Solution:
* Đăng nhập vào tài khoản của wiener, ta thấy được API key của tài khoản cũng như URL xuất hiện param id = wiener. Thay id thành carlos, ta lập tức bị đẩy về trang login
* Bắt request trước khi bị đẩy về login, ném sang Repeater, ta nhận được response chuyển hướng, kèm theo đó body là trang của carlos
<p align=center>
    <img src="./src/09_2.png">
</p>

* Submit API key cho lab, và lab được solved

<br><br>

# Lab 10: User ID controlled by request parameter with password disclosure
## Lab Description:
<p align=center>
    <img src="./src/10_1.png">
</p>

## Solution:
* Đăng nhập vào tài khoản của wiener, ta thấy được trang tài khoản cũng như URL xuất hiện param id = wiener. Thay id thành administrator, ta được tới trang của admin luôn
<p align=center>
    <img src="./src/10_2.png">
</p>

* Ném sang Repeater, ta xem được response chứa pass
<p align=center>
    <img src="./src/10_3.png">
</p>

* Đăng nhập bằng tài khoản administrator, xóa carlos, và lab đã được solved

<br><br>

# Lab 11: Insecure direct object references
## Lab Description:
## Solution:
* Vào mục Live chat, thấy có vẻ là chat với AI. Nhắn vài dòng rồi ấn View transcript, thấy tải về một file text
<p align=center>
    <img src="./src/11_2.png">
</p>

* Vào Burp, xem HTTP history thì thấy request này. Ném sang Repeater để xem response
<p align=center>
    <img src="./src/11_3.png">
</p>

* Để ý mỗi lần ấn View transcript cho 1 bản tải về với tên là số tăng dần. Vào Repeater đọc file 1.txt
<p align=center>
    <img src="./src/11_4.png">
</p>

* Copy pass để đăng nhập, và lab được solved

<br><br>

# Lab 12: Multi-step process with no access control on one step
## Lab Description
<p align=center>
    <img src="./src/12_1.png">
</p>

## Solution:
* Đăng nhập vào tài khoản administrator, vào Admin panel, thấy được chức năng thay đổi role
<p align=center>
    <img src="./src/12_2.png">
</p>

* Upgrade role của carlos lên, thấy hiện trang confirm
<p align=center>
    <img src="./src/12_3.png">
</p>

* Vào HTTP History thấy request thay đổi role có dạng như sau: action, confirmed, username
<p align=center>
    <img src="./src/12_4.png">
</p>

* Ném request đó sang Repeater rồi logout để login vào tài khoản wiener, sau đó lấy session của wiener thay vào session trong Repeater. Đổi username dưới body của request thành wiener
<p align=center>
    <img src="./src/12_5.png">
</p>

* Gửi request, và lab được solved

<br><br>

# Lab 13: Referer-based access control
## Lab Description: 
<p align=center>
    <img src="./src/13_1.png">
</p>

# Solution:
* Đăng nhập vào tài khoản administrator, vào Admin panel, thấy được chức năng thay đổi role
<p align=center>
    <img src="./src/12_2.png">
</p>

* Upgrade role của carlos lên, rồi bắt request đó ném sang Repeater

* Logout để login vào tài khoản wiener, lấy session rồi thay vào giá trị trong Repeater, đổi username thành wiener. Có thể thấy trong request có header Referer nên mới có thể gửi được
<p align=center>
    <img src="./src/13_2.png">
</p>

* Nếu ta bỏ header đó đi, ta nhận được response là Unauthorized. Gửi xong request trên và lab được solved