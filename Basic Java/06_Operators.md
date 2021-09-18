# Các toán tử trong Java
- **Java** chia các toán tử ra thành các nhóm :
    - **Arithmetic operators**
    - **Assignment operators**
    - **Comparison operators**
    - **Logical operators**
    - **Bitwise operators**
## **1) Toán tử số học - Arithmetic operators**
- Toán tử số học được sử dụng để thực hiện các phép toán cơ bản :
    
    | Toán tử | Ý nghĩa | Mô tả | Ví dụ |
    |---------|---------|-------|-------|
    | `+` | Cộng | Cộng các giá trị với nhau | `x + y` |
    | `-` | Trừ | Trừ các giá trị cho nhau | `x - y` |
    | `*` | Nhân | Nhân các giá trị với nhau | `x * y` |
    | `/` | Chia | Chia giá trị này cho giá trị kia | `x / y` |
    | `%` | Phần trăm | Trả về phần trăm nguyên của phép chia | `x % y` |
    | `++` | Increment | Tăng dần giá trị của 1 biến lên 1 đơn vị | `++x` |
    | `--` | Decrement | Giảm dần giá trị của 1 biến xuống 1 đơn vị | `--x` |
## **2) Toán tử gán - Assignment operators**
- Toán tử gán được sử dụng để gán giá trị cho một biến.

    | Toán tử | Ví dụ | Tương đương với |
    |---------|-------|-----------------|
    | `=` | `x = 5` | `x = 5` |
    | `+=` | `x += 3` | `x = x + 3` |
    | `-=` | `x -= 3` | `x = x - 3` |
    | `*=` | `x *= 3` | `x = x * 3` |
    | `/=` | `x /= 3` | `x = x / 3` |
    | `%=` | `x %= 3` | `x = x % 3` |
    | `&=` | `x &= 3` | `x = x & 3` |
    | `|=` | `x |= 3` | `x = x | 3` |
    | `^=` | `x ^= 3` | `x = x ^ 3` |
    | `>>=` | `x >>= 3` | `x = x >> 3` |
    | `<<=` | `x <<= 3` | `x = x << 3` |
## **3) Toán tử so sánh - Comparison operators**
- Toán tử so sánh được sử dụng để so sánh 2 giá trị :

    | Toán tử | Ý nghĩa | Ví dụ |
    |---------|---------|-------|
    | `==` | Bằng với | `x == y` |
    | `!=` | Không bằng với | `x != y` |
    | `>` | Lớn hơn | `x > y` |
    | `<` | Nhỏ hơn | `x < y` |
    | `>=` | Lớn hơn hoặc bằng | `x >= y` |
    | `<=` | Nhỏ hơn hoặc bằng | `x <= y` |
## **4) Toán tử Logic**
- Toán tử logic được sử dụng để xác định logic giữa biến và giá trị.

    | Toán tử | Ý nghĩa | Mô tả | Ví dụ |
    |---------|---------|-------|-------|
    | `&&` | `AND` | Trả về `true` nếu cả 2 mệnh đề đều đúng | `x < 5 &&  x < 10` |
    |  | `OR` | Trả về `true` nếu một trong các mệnh đề đúng | `x < 5`  `x < 4` |
    | `!` | `NOT` | Đảo ngược kết quả, trả về `true` nếu mệnh đề `false` | `!(x < 5 && x < 10)` |