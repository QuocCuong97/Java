# Booleans
- Trong lập trình, cần 1 kiểu dữ liệu mà chỉ chứa đúng 2 giá trị, ví dụ như :
    - `YES` / `NO`
    - `ON` / `OFF`
    - `TRUE` / `FALSE`
- Do đó, **Java** có một kiểu dữ liệu `boolean`, có thể chứa 2 loại dữ liệu `true` và `false`.
- Một kiểu dữ liệu **Boolean** được định nghĩa qua keyword `boolean` và chỉ có thể lấy giá trị `true` hoặc `false` :
    ```java
    boolean isJavaFun = true;
    boolean isFishTasty = false;
    System.out.println(isJavaFun);     // Outputs true
    System.out.println(isFishTasty);   // Outputs false
    ```
- Một mệnh đề Boolean là một mệnh đề **Java** trả về giá trị boolean : `true` hoặc `false`.
- Có thể sử dụng các toán tử so sánh, như `>` để xem mệnh đề có `true` hay `false` :
    ```java
    int x = 10;
    int y = 9;
    System.out.println(x > y); // returns true, because 10 is higher than 9
    ```
- Hoặc đơn giản hơn :
    ```java
    System.out.println(10 > 9); // returns true, because 10 is higher than 9
    ```
- Hoặc sử dụng `==` :
    ```java
    int x = 10;
    System.out.println(x == 10); // returns true, because the value of x is equal to 10
    ```
    ```java
    System.out.println(10 == 15); // returns false, because 10 is not equal to 15
    ```