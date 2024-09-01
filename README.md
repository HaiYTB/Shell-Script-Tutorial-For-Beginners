# Giới thiệu
Shell script là một tập tin chứa các lệnh và câu lệnh được viết trong một ngôn ngữ kịch bản (scripting language) của hệ điều hành, thường là bash, sh, hoặc các shell khác. Khi chạy một shell script, các lệnh bên trong tập tin sẽ được thực thi lần lượt.

**Ưu điểm:**
 - Tự động hoá
 - Quản lí hệ thống
 - Dễ học, dễ sử dụng

**Cách chạy file shell script:**
Tùy thuộc vào shebang của bạn, thông thường sẽ là:
```Shell
bash /tên/hoặc/đường/dẫn/của/file
```
hoặc
```Shell
sh /tên/hoặc/đường/dẫn/của/file
```


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

# Biến và kiểu dữ liệu của biến
Trong lập trình, **biến** (variable) là một tên gọi được sử dụng để lưu trữ và truy cập giá trị hoặc dữ liệu trong bộ nhớ của máy tính. Biến cho phép bạn lưu trữ các giá trị và sử dụng chúng ở nhiều nơi khác nhau trong chương trình.

*__Cú pháp:__*
```Bash
#!/bin/bash
tên_biến=giá_trị
```

**Ví dụ:**
```Bash
#!/bin/bash
name="Hải"
age=22
echo "Tên: $name"
echo "Tuổi: $age"
```

**Lưu ý:**
Trong shell script, bạn **không nên** đặt dấu cách xung quanh dấu bằng = khi khai báo và gán giá trị cho biến. Cú pháp chính xác không được có khoảng trắng giữa tên biến, dấu bằng, và giá trị.

**Kiểu dữ liệu của biến**
 - **Chuỗi(string)**: Kí hiệu là hai dấu ngoặc đơn(**'**) hoặc ngoặc kép(**"**). Đây là kiểu dữ liệu phổ biến nhất trong shell script. Bất kỳ giá trị nào được gán cho biến đều được xử lý như một chuỗi văn bản.
 - **Số nguyên(Integer)**: Kí hiệu là các **số nguyên**. Biến có thể chứa số nguyên và có thể được sử dụng trong các phép toán số học. Tuy nhiên, biến trong shell thực chất vẫn là chuỗi, nhưng khi bạn thực hiện các phép toán, shell sẽ xử lý chúng như số nguyên.
 - **Số thực(Float)**: Shell script không trực tiếp hỗ trợ số thực. Tuy nhiên, bạn có thể sử dụng các công cụ như bc hoặc awk để xử lý số thực.
 - **Mảng(Array)**: Shell script hỗ trợ mảng, cho phép bạn lưu trữ nhiều giá trị trong một biến duy nhất. Mảng trong shell thường là một danh sách các chuỗi ký tự.
 - **Đúng/Sai(Boolean)**: Không có kiểu dữ liệu boolean chính thức, nhưng bạn có thể sử dụng các giá trị như **true**, **false**, hoặc 1 và 0 để mô phỏng boolean trong shell script. Thường được sử dụng trong các điều kiện (if, while, until).
 - **Rỗng(Empty/Null)**: Một biến có thể được gán giá trị rỗng hoặc chưa được gán giá trị, nó sẽ được coi là biến rỗng.

*__Ví dụ__:*
String:
```Bash
#!/bin/bash
name="Hải"
echo "Tên: $name"
```
Int:
```Bash
#!/bin/bash
num1=10
num2=20
sum=$((num1 + num2))
echo "Tổng: $sum"
```
Float
```Bash
#!/bin/bash
num1=5.5
num2=2.3
sum=$(echo "$num1 + $num2" | bc)
echo "Tổng: $sum"
```
Array
```Bash
#!/bin/bash
fruits=("apple" "banana" "cherry")
echo "Trái cây thứ hai: ${fruits[1]}"
echo "Tất cả trái cây: ${fruits[@]}"
```
*Số thứ tự là từ 0 đến n*
Boolean
```Bash
#!/bin/bash
is_logged_in=true

if [ "$is_logged_in" = true ]; then
    echo "User đã đăng nhập."
else
    echo "User chưa đăng nhập."
fi
```
Null
```Bash
#!/bin/bash
empty_var=""
echo "Giá trị của biến rỗng: '$empty_var'"
```


# Comment
Trong shell script, comment (nhận xét) là các dòng không được thực thi và được sử dụng để giải thích hoặc chú thích mã nguồn cho người đọc hoặc lập trình viên khác.
Trong các script shell, bạn có thể tạo comment bằng cách sử dụng dấu #
*__Ví dụ:__*
```Bash
# Đây là một comment
echo "Hello world!" # In ra màn hình chữ Hello World!
```











