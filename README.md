# Giới thiệu
Shell script là một tập tin chứa các lệnh và câu lệnh được viết trong một ngôn ngữ kịch bản (scripting language) của hệ điều hành, thường là bash, sh, hoặc các shell khác. Khi chạy một shell script, các lệnh bên trong tập tin sẽ được thực thi lần lượt.

**Ưu điểm**
 - Tự động hoá
 - Quản lí hệ thống
 - Dễ học, dễ sử dụng

**Cấu trúc cơ bản**
# Shebang
Một shell script thường bắt đầu với dòng shebang để chỉ định shell nào sẽ được sử dụng để chạy script. Ví dụ:
*Bash shell Linux*
```Bash
#!/bin/bash
```
*Python*
```Bash
#!/usr/bin/env python3
```
(Shebang này sẽ tìm Python theo đường dẫn môi trường thay vì chỉ định đường dẫn cố định)

Mục đích chính của shebang là để chỉ định trình thông dịch.

**Sử dụng shebang với mục đích:**
 - Đa nền tảng: Khi script của bạn được chia sẻ hoặc chạy trên các hệ thống khác nhau, shebang đảm bảo rằng nó sẽ được thực thi với đúng trình thông dịch, bất kể môi trường nào.
 - Tính đồng nhất: Đảm bảo rằng cùng một script sẽ chạy theo cùng một cách trên mọi hệ thống, miễn là trình thông dịch được chỉ định có sẵn.
