# Giới thiệu
Shell script là một tập tin chứa các lệnh và câu lệnh được viết trong một ngôn ngữ kịch bản (scripting language) của hệ điều hành, thường là bash, sh, hoặc các shell khác. Khi chạy một shell script, các lệnh bên trong tập tin sẽ được thực thi lần lượt.

**Ưu điểm**
 - Tự động hoá
 - Quản lí hệ thống
 - Dễ học, dễ sử dụng

# Shebang
Một shell script thường bắt đầu với dòng shebang để chỉ định shell nào sẽ được sử dụng để chạy script. Ví dụ:
*__Bash shell Linux__*
```Bash
#!/bin/bash
```
*__Python__*
```Bash
#!/usr/bin/env python3
```
(Shebang này sẽ tìm Python theo đường dẫn môi trường thay vì chỉ định đường dẫn cố định)

Mục đích chính của shebang là để chỉ định trình thông dịch.

**Sử dụng shebang với mục đích:**
 - Đa nền tảng: Khi script của bạn được chia sẻ hoặc chạy trên các hệ thống khác nhau, shebang đảm bảo rằng nó sẽ được thực thi với đúng trình thông dịch, bất kể môi trường nào.
 - Tính đồng nhất: Đảm bảo rằng cùng một script sẽ chạy theo cùng một cách trên mọi hệ thống, miễn là trình thông dịch được chỉ định có sẵn.


# In ra màn hình với echo và printf
**echo**
*__Cấu trúc:__*
```Bash
#!/bin/bash
echo [tuỳ chọn] giá_trị_cần_in
```
*Các tùy chọn của echo:*
 - **-n**: Tùy chọn này yêu cầu echo không tự động thêm ký tự dòng mới (newline) sau khi in chuỗi ra màn hình.
 - **-e**: Cho phép echo xử lý các ký tự đặc biệt như: \n, \t, ...

**printf**
*__Cấu trúc:__*
```Bash
#!/bin/bash
printf giá_trị_cần_in [danh sách các giá trị]
```
*Danh sách các giá trị:*
 - **%s**: Chuỗi (string).
 - **%d**: Số nguyên (integer).
 - **%f**: Số thực (float).
 - **%x**: Số nguyên dạng thập lục phân (hexadecimal).

**Ví dụ:**
*echo*
```Bash
#!/bin/bash
echo "Hello, World!"
```

*printf*
```Bash
#!/bin/bash
printf "Tên: %s, Tuổi: %d\n" "Hải" 22
```

**Khi nào nên sử dụng echo, khi nào nên sử dụng printf?**
*__Sử dụng **echo** khi:__*
 - In chuỗi đơn giản
 - Cần in ra nhanh chóng
 - Thêm dòng mới tự động
 - Không cần kiểm soát chi tiết

*__Sử dụng **printf** khi:__*
 - Cần định dạng chi tiết
 - Không muốn tự động thêm dòng mới
 - In dữ liệu theo nhiều định dạng/kiểu dữ liệu khác nhau
 - Cần kiểm soát chính xác về khoảng trắng và căn chỉnh
*Dùng echo khi bạn cần in văn bản đơn giản, nhanh chóng, không cần định dạng phức tạp. Dùng printf Khi bạn cần kiểm soát chi tiết hơn về định dạng, kiểu dữ liệu, hoặc cần output phức tạp và chính xác.*
