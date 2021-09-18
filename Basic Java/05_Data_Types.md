# Kiểu dữ liệu trong Java
## **1) Giới thiệu**
- Kiểu dữ liệu là là tập hợp các nhóm dữ liệu có chung đặc tính, cách lưu trữ và thao tác xử lý. Nhờ có kiểu dữ liệu thì compiler nhận biết được kích thước của một biến và khả năng lưu trữ của nó.
- Lý do phải có kiểu dữ liệu :
    - Biến cần có bộ nhớ dành riêng để lưu trữ giá trị. Nghĩa nào khi bạn khai báo biến bạn cần dữ trữ không gian cho bộ nhớ.
    - Dựa vào kiểu dữ liệu của biến, hệ điều hành sẽ cấp bộ nhớ và quyết định thứ gì có thể lưu trữ ở bộ nhớ đã cho. Như biến có kiểu dữ liệu số nguyên, số thức hay kí tự thì hệ điều hành sẽ xác định vùng nhớ đó lưu giá trị như thế nào.
## **2) Phân loại các kiểu dữ liệu**
- **Java** tồn tại 2 loại kiểu dữ liệu :
    - Các kiểu dữ liệu nguyên thủy (Primitive Data Types)
    - Các kiểu dữ liệu tham chiếu (Reference Types)
### **2.1) Primitive Data Types**
- Có đến 8 kiểu dữ liệu **primitive** trong **Java**. Kiểu dữ liệu **Primitive** đã được đặt ra trước và tên nó nằm trong từ khóa của **Java** :
    - **Boolean** :
        - Kiểu **Boolean** chỉ sử dụng lưu trữ cho 2 giá trị: `true` và `false`. Mục đích kiểu **Boolean** thường được cho những câu điều kiện rẽ nhánh.
        - **VD :**
            ```java
            Boolean isDone = false
            ```
    - **Byte** :
        - Kiểu dữ liệu **Byte** dùng để lưu trữ kiểu số nguyên có kích cỡ bằng `1 byte` (`8 bit`). Giá trị có thể lưu được nằm trong khoảng từ `-128` (`-2^7`) đến `127` (`2^7-1`).
        - **VD :**
            ```java
            byte a = 100
            ```
    - **Short** :
        - Kiểu dữ liệu **Short** dùng để lưu trữ kiểu số nguyên có kích cỡ bằng `2 byte` (`16 bit`). Giá trị có thể lưu được nằm trong khoảng từ `-32,768` (`-2^15`) đến `32,767` (`2^15-1`).
        - **VD :**
            ```java
            short a = 10000
            ```
    - **Int** :
        - Kiểu dữ liệu **Int** dùng để lưu trữ kiểu số nguyên có kích cỡ bằng `4 byte` (`32 bit`). Giá trị có thể lưu được nằm trong khoảng từ `-2,147,483,648` (`-2^31`) đến `2,147,483,647` (`2^31-1`).
        - **VD :**
            ```java
            int a = 20000000
            ```
    - **Long** :
        - Kiểu dữ liệu **Long** dùng để lưu trữ kiểu số nguyên có kích cỡ bằng `8 byte`. Giá trị có thể lưu được nằm trong khoảng từ `-9,223,372,036,854,775,808` (`-2^63`) đến `9,223,372,036,854,775`,807 (`2^63-1`). Giá trị gán cần có kí tự "`l`" phía sau.
        - **VD :**
            ```java
            long a = 1001000l
            ```
    - **Float** :
        - Kiểu dữ liệu **Float** dùng để lưu trữ số thực có kích cỡ bằng `4 byte` (`32 bit`). Giá trị có thể lưu được nằm trong khoảng từ `-3.4028235 x 10^38` đến `-3.4028235 x 10^38`. Giá trị gán cần có kí tự "`f`" phía sau.
        - **VD :**
            ```java
            float a = 2.51f
            ```
    - **Double** :
        - Kiểu dữ liệu **Double** dùng để lưu trữ số thực có kích cỡ bằng `8 byte` (`64 bit`). Giá trị có thể lưu nằm trong khoảng từ `-1.7976931348623157 x 10^308` đến `-1.7976931348623157 x 10^308`. Giá trị gán có thể có hoặc không kí tự "`d`" phía sau.
        - **VD :**
            ```java
            double a = 2.52.d hoặc double a = 2.52
            ```
    - **Char** :
        - Kiểu dữ liệu **Char** dùng để lưu trữ kí tự có kích cỡ bằng `2 byte`. Bản chất **Char** lưu trữ code Unicode nhưng khi lại hiển thị ra "kí tự" ứng với mã đó. Giá trị có thể lưu trữ nằm trong khoảng "`u0000`" đến "`uffff`".
### **2.2) Reference Types**
- Kiểu dữ liệu tham chiếu là kiểu dữ liệu của đối tượng. Biến của kiểu dữ liệu tham chiếu chỉ chứa địa chỉ của đối tượng dữ liệu tại bộ nhớ **Stack**. Đối tượng dữ liệu lại nằm ở bộ nhớ **Heap**. Một số kiểu dữ liệu cụ thể như các mảng (Array), lớp đối tượng (Class) hay kiểu lớp giao tiếp (Interface).

    <p align=center><img src=https://i.imgur.com/2SRHKT0.png width=40%></p>

- Kiểu dữ liệu **primitive** được định nghĩa trước trong **Java**. Các kiểu **reference** được tạo bởi lập trình viên và không được định nghĩa bởi **Java** (ngoại trừ **String**)
- Kiểu dữ liệu **reference** có thể được sử dụng để gọi các phương thức thực hiện một số action nhất định, trong khi các kiểu **primitive** thì không.
- Kiểu dữ liệu **primitive** luôn phải có giá trị, trong khi các kiểu **reference** có thể có giá trị là `null`.
- Kiểu dữ liệu **primitive** bắt đầu bằng chữ thường, trong khi các kiểu **reference** bắt đầu bằng chữ hoa. 
- Kích thước của kiểu dữ liệu **primitive** phụ thuộc vào kiểu dữ liệu, trong khi các kiểu **reference** có cùng kích thước.
## **3) Ép kiểu dữ liệu**
- **Ép kiểu** là cách chuyển biến thuộc kiểu dữ liệu này thành biến thuộc kiểu dữ liệu khác.
- Ý nghĩa:
    - Việc chuyển kiểu dữ liệu sẽ đến lúc phải cần trong quá trình xử lý chương trình
    - Có thể định dạng đúng kiểu dữ liệu mình mong muốn (Như cách hiển thị kiểu ngày tháng năm trên thế giới khác với Việt Nam nên ta sẽ chuyển kiểu ngày theo phong cách địa phương).
- Ở đây ta chỉ nói đến ép kiểu dữ liệu đối với dữ liệu nguyên thủy (**Primitive Data Types**), còn đối với ép kiểu dữ liệu tham chiếu (**Reference Types**) thì cách ép kiểu là những hàm (phương thức) ép kiểu do người ta viết riêng cho mỗi kiểu dữ tham chiếu đó.
- Trong kiểu dữ liệu nguyên thủy được chia ra làm 2 loại:
    - ***Widening Casting*** (tự động) - convert những kiểu dữ liệu nhỏ thành kiểu dữ liệu lớn hơn.
        ```
        byte -> short -> char -> int -> long -> float -> double
        ```
        - **VD :**
            ```java
            public class Main {
                public static void main(String[] args) {
                    int myInt = 9;
                    double myDouble = myInt; // Automatic casting: int to double

                    System.out.println(myInt);      // Outputs 9
                    System.out.println(myDouble);   // Outputs 9.0
                }
            }
    - ***Narrowing Casting*** (manual) - convert kiểu dữ liệu lớn hơn thành nhỏ hơn
        ```
        double -> float -> long -> int -> char -> short -> byte
        ```
        - **VD :**
            ```java
            public class Main {
                public static void main(String[] args) {
                    double myDouble = 9.78d;
                    int myInt = (int) myDouble; // Manual casting: double to int

                    System.out.println(myDouble);   // Outputs 9.78
                    System.out.println(myInt);      // Outputs 9
                }
            }
            ```