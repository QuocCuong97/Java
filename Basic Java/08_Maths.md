# Các phương thức toán học trong Java
- Class Java Math có nhiều phương thức cho phép thực hiện các phép toán số học.
### **`Math.max(x,y)`**
- Phương thức `Math.max(x,y)` có thể được sử dụng để tìm giá trị cao nhất giữa `x` và `y` :
    ```java
    Math.max(5, 10);
    ```
### **`Math.min(x,y)`**
- Phương thức `Math.min(x,y)` có thể được sử dụng để tìm giá trị nhỏ nhất giữa `x` và `y` :
    ```java
    Math.min(5, 10);
    ```
### **`Math.sqrt(x)`**
- Phương thức `Math.sqrt(x)` có thể được sử dụng để tìm căn bậc 2 của `x` :
    ```java
    Math.sqrt(64);
    ```
### **`Math.abs(x)`**
- Phương thức `Math.abs(x)` trả về giá trị tuyệt đối của `x` :
    ```java
    Math.abs(-4.7);
    ```
### **Số ngẫu nhiên**
- Phương thức `Math.random()` trả về một số ngẫu nhiên giữa `0.0` và `1.0`
    ```java
    Math.random();
    ```
- Có thể lấy số ngẫu nhiên giữa `0` và `100` sử dụng cách sau :
    ```java
    int randomNum = (int)(Math.random() * 101);    // 0 to 100
    ```