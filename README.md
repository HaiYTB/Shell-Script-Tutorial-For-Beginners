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


# Ép kiểu dữ liệu của biến
Trong shell script, ép kiểu dữ liệu (type casting) không được thực hiện theo cách trực tiếp như trong các ngôn ngữ lập trình mạnh mẽ hơn. Tuy nhiên, bạn có thể làm việc với các biến bằng cách chuyển đổi giữa các kiểu dữ liệu thông qua các phép toán và các kỹ thuật khác.

**Ép kiểu chuỗi(str) sang số(int):**
```Bash
#!/bin/bash

num_str="42"

# Thực hiện phép toán với chuỗi số; shell sẽ ép kiểu chuỗi thành số
result=$((num_str + 8))

echo "Kết quả: $result"
```

**Ép kiểu số(int) sang chuỗi(str):**
```Bash
#!/bin/bash

num=123

# Ép kiểu số thành chuỗi
str="$num"

echo "Chuỗi: $str"
```

**Chuyển đổi kiểu trong các phép toán:**
```Bash
#!/bin/bash

num_str="15"
num_int=5

# Thực hiện phép toán, ép kiểu chuỗi thành số
result=$((num_str + num_int))

echo "Kết quả phép toán: $result"
```


# Comment
Trong shell script, comment (nhận xét) là các dòng không được thực thi và được sử dụng để giải thích hoặc chú thích mã nguồn cho người đọc hoặc lập trình viên khác.
Trong các script shell, bạn có thể tạo comment bằng cách sử dụng dấu #

*__Ví dụ:__*
```Bash
# Đây là một comment
echo "Hello world!" # In ra màn hình chữ Hello World!
```


# Đọc dữ liệu đầu vào từ người dùng
Đọc dữ liệu từ người dùng trong shell script có thể được thực hiện bằng cách sử dụng lệnh read. Lệnh read cho phép bạn nhận đầu vào từ người dùng và lưu trữ vào một biến để sử dụng sau này trong script.

*__Ví dụ:__*
```Bash
#!/bin/bash

# Yêu cầu người dùng nhập tên
echo "Nhập tên của bạn:"
read name

# Hiển thị tên của người dùng
echo "Chào, $name!"
```
Trong ví dụ trên:
 - Lệnh echo hiển thị một thông báo yêu cầu người dùng nhập dữ liệu.
 - Lệnh read nhận đầu vào từ người dùng và lưu trữ vào biến name.
 - Cuối cùng, echo sử dụng biến name để hiển thị lời chào.

Bạn cũng có thể đọc nhiều giá trị cùng lúc và đặt các giá trị đó vào các biến khác nhau.

*__Ví dụ:__*
```Bash
#!/bin/bash

# Yêu cầu người dùng nhập tên và tuổi
echo "Nhập tên của bạn và tuổi của bạn:"
read name age

# Hiển thị thông tin của người dùng
echo "Chào, $name! Bạn $age tuổi."
```

Cờ -p trong lệnh read cho phép bạn cung cấp một thông báo (prompt) trực tiếp ngay khi yêu cầu người dùng nhập dữ liệu, thay vì sử dụng lệnh echo riêng biệt.

*__Ví dụ:__*
```Bash
#!/bin/bash

# Sử dụng cờ -p để cung cấp thông báo nhập dữ liệu
read -p "Nhập tên của bạn: " name

# Hiển thị tên của người dùng
echo "Chào, $name!"
```

Trong ví dụ trên:
 - Cờ -p cho phép bạn cung cấp thông báo "Nhập tên của bạn: " trực tiếp trong lệnh read.
 - Người dùng nhập dữ liệu sau thông báo đó, và giá trị đó được lưu trữ trong biến name.

**Lưu ý:**
Cờ -p trong lệnh read được hỗ trợ từ phiên bản bash 3.2 trở đi. Nếu bạn sử dụng bash phiên bản cũ hơn hoặc một shell khác như sh, cờ -p có thể không được hỗ trợ.


# Truyền tham số(pass agurments)
Trong shell script, "pass arguments" (truyền tham số) là cách bạn cung cấp dữ liệu cho script khi chạy nó. Các tham số này có thể được sử dụng trong script để thực hiện các thao tác cụ thể.

*__Trong script bạn có thể truy cập tham số bằng các biến đặt biệt:__*
 - $1 đến $9 cho các tham số từ 1 đến 9.
 - ${10} và các tham số tiếp theo được truy cập bằng cách sử dụng cú pháp ${n}, trong đó n là số thứ tự của tham số.

*__Ví dụ:__*
```Shell
bash pass_args.sh Hải HaiTool HaiYTB
```
Với file pass_args.sh:
```Bash
#!/bin/bash

# Truy cập tham số
echo "Tham số đầu tiên: $1"
echo "Tham số thứ hai: $2"
echo "Tham số thứ ba: $3"

# Số lượng tham số
echo "Số lượng tham số: $#"

# Tất cả các tham số
echo "Tất cả tham số: $*"
```

*Output:*
```
Tham số đầu tiên: Hải
Tham số thứ hai: HaiTool
Tham số thứ ba: HaiYTB
Số lượng tham số: 3
Tất cả tham số: Hải HaiTool HaiYTB
```


# Toán tử
**Toán tử số học:**
 - **+** : Cộng
 - **-** : Trừ
 - __*__ : Nhân
 - **/** : Chia
 - **%** : Chia lấy dư

**Toán tử so sánh (sử dụng trong [ ] hoặc [[ ]]):**
 *__So sánh số nguyên:__*
  - **-eq** : Bằng
  - **-ne** : Khác
  - **-lt** : Nhỏ hơn
  - **-le** : Nhỏ hơn hoặc bằng
  - **-gt** : Lớn hơn
  - **-ge** : Lớn hơn hoặc bằng
 *__So sánh chuỗi:__*
  - **=** : Bằng
  - **!=** : Khác
  - **<** : Nhỏ hơn (trong [[ ]])
  - **>** : Lớn hơn (trong [[ ]])

**Toán tử logic (sử dụng trong [ ] hoặc [[ ]]):**
 - **-a** : AND - VÀ (trong [ ])
 - **-o** : OR - HOẶC (trong [ ])
 - **&&** : AND - VÀ (trong [[ ]] và giữa các câu lệnh)
 - **||** : OR - HOẶC (trong [[ ]] và giữa các câu lệnh)
 - **!** : NOT - KHÔNG(KHÔNG PHẢI)

**Toán tử kiểm tra file:**
 - **-e file**: Kiểm tra xem file có tồn tại không.
 - **-f file**: Kiểm tra xem file có phải là một file bình thường không.
 - **-d file**: Kiểm tra xem file có phải là một thư mục không.
 - **-r file**: Kiểm tra xem file có thể đọc được không.
 - **-w file**: Kiểm tra xem file có thể ghi được không.
 - **-x file**: Kiểm tra xem file có thể thực thi được không.
 - **-s file**: Kiểm tra xem file có kích thước lớn hơn 0 byte không.
 - **-L file**: Kiểm tra xem file có phải là liên kết mềm không.

*__Ví dụ:__*
```Bash
#!/bin/bash
a=10
b=5
c="Hello"
d="Hello"
f="Hi"
sum=$((a + b))
echo "Tổng: $sum"  # Kết quả: Tổng: 15

difference=$((a - b))
echo "Hiệu: $difference"  # Kết quả: Hiệu: 5

product=$((a * b))
echo "Tích: $product"  # Kết quả: Tích: 50

quotient=$((a / b))
echo "Thương: $quotient"  # Kết quả: Thương: 2

remainder=$((a % b))
echo "Dư: $remainder"  # Kết quả: Dư: 0

if [ $a -eq $b ]; then
    echo "a bằng b"
else
    echo "a không bằng b"  # Kết quả: a không bằng b
fi

if [ $a -ne $b ]; then
    echo "a khác b"  # Kết quả: a khác b
fi

if [ $a -ne $b ]; then
    echo "a khác b"  # Kết quả: a khác b
fi

if [ $a -lt $b ]; then
    echo "a nhỏ hơn b"
else
    echo "a không nhỏ hơn b"  # Kết quả: a không nhỏ hơn b
fi

if [ $a -le $b ]; then
    echo "a nhỏ hơn hoặc bằng b"
else
    echo "a lớn hơn b"  # Kết quả: a lớn hơn b
fi

if [ $a -gt $b ]; then
    echo "a lớn hơn b"  # Kết quả: a lớn hơn b
fi

if [ $a -ge $b ]; then
    echo "a lớn hơn hoặc bằng b"  # Kết quả: a lớn hơn hoặc bằng b
fi

if [ "$c" = "$d" ]; then
    echo "c bằng d"  # Kết quả: c bằng d
fi

if [ "$c" != "$f" ]; then
    echo "c khác f"  # Kết quả: c khác f
fi

if [[ "$c" < "$f" ]]; then
    echo "c nhỏ hơn f"
else
    echo "c không nhỏ hơn f"  # Kết quả: c không nhỏ hơn f
fi

if [[ "$f" > "$c" ]]; then
    echo "f lớn hơn c"  # Kết quả: f lớn hơn c
fi

if [ $a -gt 0 -a $b -lt 10 ]; then
    echo "a lớn hơn 0 và b nhỏ hơn 10"  # Kết quả: a lớn hơn 0 và b nhỏ hơn 10
fi

if [ $a -lt 0 -o $b -lt 10 ]; then
    echo "a nhỏ hơn 0 hoặc b nhỏ hơn 10"  # Kết quả: a nhỏ hơn 0 hoặc b nhỏ hơn 10
fi

if [[ $a -gt 0 && $b -lt 10 ]]; then
    echo "a lớn hơn 0 và b nhỏ hơn 10"  # Kết quả: a lớn hơn 0 và b nhỏ hơn 10
fi

if [[ $a -lt 0 || $b -lt 10 ]]; then
    echo "a nhỏ hơn 0 hoặc b nhỏ hơn 10"  # Kết quả: a nhỏ hơn 0 hoặc b nhỏ hơn 10
fi

if [ ! $a -lt 0 ]; then
    echo "a không nhỏ hơn 0"  # Kết quả: a không nhỏ hơn 0
fi

file="example.txt"

if [ -e "$file" ]; then
    echo "$file tồn tại."

    if [ -f "$file" ]; then
        echo "$file là một file bình thường."
    elif [ -d "$file" ]; then
        echo "$file là một thư mục."
    fi

    if [ -r "$file" ]; then
        echo "$file có thể đọc được."
    fi

    if [ -w "$file" ]; then
        echo "$file có thể ghi được."
    fi

    if [ -x "$file" ]; then
        echo "$file có thể thực thi được."
    fi
else
    echo "$file không tồn tại."
fi
```

**LƯU Ý:**
Trong shell script, [] và () có những công dụng khác nhau, chủ yếu trong các tình huống so sánh và thực thi lệnh.

[] là một cách để kiểm tra các điều kiện trong shell script.
() được sử dụng để nhóm các lệnh lại với nhau và thực thi chúng trong một subshell(môi trường con)


# Cấu trúc rẽ nhánh(if, else, elif) - Câu lệnh điều kiện loại 1
Câu lệnh if là công cụ chính để kiểm tra điều kiện và thực hiện các lệnh dựa trên kết quả của điều kiện đó.

*__Cấu trúc:__*
```Bash
if [ điều kiện ]; then
    # Lệnh sẽ được thực thi nếu điều kiện là true
elif [ điều kiện khác ]; then
    # Lệnh sẽ được thực thi nếu điều kiện đầu tiên là false và điều kiện này là true
else
    # Lệnh sẽ được thực thi nếu tất cả các điều kiện trên đều false
fi
```

*__Ví dụ:__*
```Bash
#!/bin/bash

echo "Nhập một số:"
read num

if [ $num -gt 0 ]; then
    echo "Số dương"
elif [ $num -lt 0 ]; then
    echo "Số âm"
else
    echo "Số không"
fi
```


# case - Câu lệnh điều kiện loại 2
Câu lệnh case cho phép bạn thực hiện các lệnh dựa trên giá trị của biến.

*__Cấu trúc:__*
```Bash
case $biến in
    giá_trị_1)
        # Các lệnh thực hiện khi biến có giá trị giá_trị_1
        ;;
    giá_trị_2)
        # Các lệnh thực hiện khi biến có giá trị giá_trị_2
        ;;
    *)
        # Các lệnh thực hiện khi biến không khớp với bất kỳ giá trị nào ở trên
        ;;
esac
```

*__Ví dụ:__*
```Bash
#!/bin/bash

day="Monday"

case $day in
    Monday)
        echo "Hôm nay là thứ hai"
        ;;
    Friday)
        echo "Hôm nay là thứ sáu"
        ;;
    *)
        echo "Ngày không xác định"
        ;;
esac
```


# Vòng lặp
**Vòng lặp while**
Vòng lặp while trong shell script cho phép bạn lặp lại một khối lệnh trong khi một điều kiện nhất định là đúng.

*__Cú pháp:__*
```Bash
while [ điều_kiện ]; do
    # Các lệnh thực hiện trong vòng lặp
done
```

*__Ví dụ__:*
```Bash
#!/bin/bash

counter=1

while [ $counter -le 5 ]; do
    echo "Số: $counter"
    counter=$((counter + 1))  # Tăng giá trị biến counter
done
```

**Vòng lặp for**
Vòng lặp for trong shell script cho phép bạn lặp qua một danh sách các giá trị hoặc qua một dải số, và thực hiện một khối lệnh cho mỗi giá trị trong danh sách hoặc dải số.

*__Cấu trúc__:*
*Vòng lặp for với các (biến) danh sách giá trị:*
```Bash
for item in giá_trị_1 giá_trị_2 giá_trị_3; do
    # Các lệnh thực hiện cho mỗi giá trị
done
```
hoặc
```Bash
# Khởi tạo mảng
array=("value1" "value2" "value3")

# Lặp qua các phần tử của mảng
for item in "${array[@]}"; do
    echo "Item: $item"
done
```
Ví dụ:
```Bash
#!/bin/bash

for fruit in apple banana cherry; do
    echo "Fruit: $fruit"
done
```

*Vòng lặp for qua dải số:*
```Bash
for number in {bắt_đầu..kết_thúc}; do
    # Các lệnh thực hiện cho mỗi số
done
```
Ví dụ
```Bash
#!/bin/bash

for number in {1..5}; do
    echo "Number: $number"
done
```

*Vòng lặp for với cú pháp C-style:*
```Bash
for ((biến = giá_trị_bắt_đầu; điều_kiện; biến = biến + bước)); do
    # Các lệnh thực hiện cho mỗi giá trị
done
```
Ví dụ:
```Bash
#!/bin/bash

for ((i = 1; i <= 5; i++)); do
    echo "Number: $i"
done
```

**Vòng lặp với break và continue**
- **break**: Để thoát khỏi vòng lặp.
- **continue**: Để bỏ qua phần còn lại của vòng lặp và tiếp tục với vòng lặp tiếp theo.

*__Ví dụ:__*
```Bash
#!/bin/bash

counter=1

while [ $counter -le 10 ]; do
    if [ $counter -eq 5 ]; then
        echo "Đến số 5, thoát khỏi vòng lặp."
        break
    fi

    if [ $counter -eq 3 ]; then
        counter=$((counter + 1))
        continue
    fi

    echo "Số: $counter"
    counter=$((counter + 1))
done
```


# Hàm
Trong shell script, hàm (function) là một cách để tổ chức mã nguồn và tái sử dụng các đoạn mã. Bạn có thể định nghĩa và gọi hàm để thực hiện các tác vụ cụ thể.

*__Cấu trúc:__*
*Cách 1: Truyền thống:*
```Bash
function_name() {
    # Các lệnh thực hiện trong hàm
}
```

*Cách 2: Sử dụng từ khoá function:*
```Bash
function function_name {
    # Các lệnh thực hiện trong hàm
}
```

*__Ví dụ:__*
```Bash
#!/bin/bash

Hello() {
    echo "Hello, $1!"
}

Hello "Hải"
```
hoặc
```Bash
#!/bin/bash

function Hello {
    echo "Hello, $1!"
}

Hello "HaiYTB"
```

**Tham số và biến trong hàm**
Hàm có thể nhận tham số và sử dụng các **biến nội bộ**:
 - $1, $2, ..., $N là các tham số truyền vào hàm.
 - $@ hoặc $* đại diện cho tất cả các tham số.

*__Cách gọi hàm:__*
```Bash
tên_hàm [tham số 1] [tham số 2] [tham số...n]
```

*__Ví dụ:__*
```Bash
#!/bin/bash

Sums() {
    local sum=$(( $1 + $2 ))
    echo "Sum: $sum"
}

Sums 5 10
```

**Trả giá trị từ hàm**
*__Ví dụ:__*
```Bash
#!/bin/bash

multiply_numbers() {
    local product=$(( $1 * $2 ))
    echo $product
}

result=$(multiply_numbers 4 5)
echo "Product: $result"
```

**Biến cục bộ và toàn cục**
- **Biến cục bộ**: Sử dụng từ khóa **local** để khai báo biến chỉ có hiệu lực trong hàm.

*__Ví dụ:__*
```Bash
#!/bin/bash

increment() {
    local number=$1
    number=$(( number + 1 ))
    echo $number
}

value=10
new_value=$(increment $value)
echo "Original: $value, Incremented: $new_value"
```

**Hàm có giá trị trả về**
*__Ví dụ:__*
```Bash
#!/bin/bash

calculate_square() {
    local num=$1
    echo $(( num * num ))
}

square=$(calculate_square 6)
echo "Square: $square"
```
