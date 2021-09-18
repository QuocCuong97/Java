# Các biến trong Java
- Mục đích của **biến** chính là ***lưu trữ dữ liệu*** và ***tái sử dụng***. Bản chất **biến** là một tên gọi tham chiếu đến vùng nhớ nào đó trong bộ nhớ. Vì bộ nhớ lưu nhiều thông tin nên bạn muốn phân biệt để lấy thông tin nào thì phải cần **biến** để gọi nó.
## **1) Các kiểu dữ liệu trong Java**
- Trong **Java** có các kiểu dữ liệu khác nhau như :
    - **String** - lưu trữ text, ví dụ như `"Hello"`. String được bao quanh bởi cặp dấu `""`
    - **Int** - lưu trữ số nguyên, không chứa dấu phẩy. **VD :** `123` hay `-123`
    - **Float** - lưu trữ số thực, số thập phân (chứa dấu phẩy). **VD :** `19.99` hoặc `-19.99`
    - **Char** - lưu trữ các ký tự riêng, như `'a'` hoặc `'B'`. Char được bao quanh bởi cặp dấu `''`
    - **Boolean** - lưu trữ giá trị ở 2 trạng thái `true` hoặc `false`
## **2) Cách khai báo và sử dụng biến**
- Cú pháp :
    ```
    type variable = value;
    ```
    - Trong đó :
        - `type` : kiểu dữ liệu (chẳng hạn như **Int** hoặc **String**)
        - `variable` : tên biến
        - `value` : giá trị của biến
- **VD1 :** Tạo 1 biến lưu trữ string :
    ```java
    String name = "John";
    System.out.println(name);
    ```
    - Output : `John`
- **VD2 :** Tạo 1 biến lưu trữ number :
    ```java
    int myNum = 15;
    System.out.println(myNum);
    ```
    - Output : `15`
- **VD3 :** Tạo biến trước và assign giá trị sau :
    ```java
    int myNum;
    myNum = 15;
    System.out.println(myNum);
    ```
    - Output : `15`
- **VD4 :** Ghi đè giá trị của biến sau khi khai báo :
    ```java
    int myNum = 15;
    myNum = 20;  // myNum is now 20
    System.out.println(myNum);
    ```
- Có thể sử dụng keyword `final` nếu muốn set biến là hằng số (constant), giá trị biến không bị thay đổi khi ghi đè :
    ```java
    final int myNum = 15;
    myNum = 20;
    ```
    - Output : `error: cannot assign a value to final variable myNum`
## **3) Hiển thị giá trị của biến**
- Phương thức `println()` thường được sử dụng để hiển thị giá trị của biến
- Để kết hợp text và một biến, sử dụng toán tử `+` :
    ```java
    String name = "John";
    System.out.println("Hello " + name);
    ```
    - Output : `Hello John`
- Cũng có thể sử dụng toán tử `+` để gộp 2 biến string :
    ```java
    String firstName = "John ";
    String lastName = "Doe";
    String fullName = firstName + lastName;
    System.out.println(fullName);
    ```
    - Output : `John Doe`
- Với các biến numberic, toán tử `+` sẽ được coi như một phép toán cộng (lưu ý chỉ sử dụng cho biến **Int**) :
    ```java
    int x = 5;
    int y = 6;
    System.out.println(x + y); // Print the value of x + y
    ```
    - Output : `11`
## **4) Khai báo nhiều biến cùng lúc**
- Để khai báo nhiều hơn một biến sử dụng cùng kiểu dữ liệu, có thể dùng dấu "`,`" để phân tách giữa các biến.
    ```java
    int x = 5, y = 6, z = 50;
    System.out.println(x + y + z);
    ```
    - Output : `61`
## **5) Quy tắc đặt tên biến**
- Tất cả các biến **Java** phải là duy nhất
- Tên biến có thể là shortname (`x`, `y`) hoặc tên chi tiết hơn (`age`, `sum`, `totalVolume`).
    ```java
    int minutesPerHour = 60;
    ```
- Tên biến có thể chứa ký tự, chữ số, dấu "`_`", dấu "`$`".
- Tên biến phải bắt đầu bằng một chữ cái.
- Tên biến phải bắt đầu bằng chữ thường và không chứa khoảng trắng.
- Tên biến cũng có thể bắt đầu bằng "`_`" hoặc "`$`".
- Tên biến phân biệt chữ hoa và chữ thường (ví dụ "`myVar`" và "`myvar`" là 2 biến khác nhau)
- Các keyword của **Java** không được sử dụng để đặt tên biến.