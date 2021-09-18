# Mệnh đề If...else
- **Java** hỗ trợ các mệnh đề điều kiện sau :
    - Sử dụng `if` để chỉ định đoạn code cần thực thi, nếu điều kiện `true`
    - Sử dụng `else` để chỉ định đoạn code cần thực thi, nếu điều kiện `false`
    - Sử dụng `else if` để chỉ định điều kiện để kiểm tra, nếu điều kiện đầu tiên `false`
    - Sử dụng `switch` để chỉ định block code thay thế nhau được thực hiện
### **Mệnh đề `if`**
- Sử dụng mệnh đề `if` để chỉ định đoạn code cần thực thi, nếu điều kiện `true`.
- Cú pháp :
    ```java
    if (condition) {
        // block of code to be executed if the condition is true
    }
    ```
- **VD1 :**
    ```java
    if (20 > 18) {
        System.out.println("20 is greater than 18");
    }
    ```
- **VD2 :**
    ```java
    int x = 20;
    int y = 18;
    if (x > y) {
        System.out.println("x is greater than y");
    }
    ```
### **Mệnh đề `else`**
- Sử dụng mệnh đề `else` để chỉ định đoạn code cần thực thi, nếu điều kiện `false`
- Cú pháp :
    ```java
    if (condition) {
        // block of code to be executed if the condition is true
    } else {
        // block of code to be executed if the condition is false
    }
    ```
- **VD :**
    ```java
    int time = 20;
    if (time < 18) {
        System.out.println("Good day.");
    } else {
        System.out.println("Good evening.");
    }
    // Outputs "Good evening."
    ```
### **Mệnh đề `else if`**
- Sử dụng mệnh đề `else if` để chỉ định điều kiện để kiểm tra, nếu điều kiện đầu tiên `false`
- Cú pháp :
    ```java
    if (condition1) {
        // block of code to be executed if condition1 is true
    } else if (condition2) {
        // block of code to be executed if the condition1 is false and condition2 is true
    } else {
        // block of code to be executed if the condition1 is false and condition2 is false
    }
    ```
- **VD :**
    ```java
    int time = 22;
    if (time < 10) {
        System.out.println("Good morning.");
    } else if (time < 20) {
        System.out.println("Good day.");
    } else {
        System.out.println("Good evening.");
    }
    // Outputs "Good evening."
    ```
### **Rút ngắn mệnh đề `If...else`**
- Cú pháp :
    ```java
    variable = (condition) ? expressionTrue :  expressionFalse;
    ```
- **VD :**
    ```java
    int time = 20;
    if (time < 18) {
        System.out.println("Good day.");
    } else {
        System.out.println("Good evening.");
    }
    ```
    - Có thể thay bằng :
    ```java
    int time = 20;
    String result = (time < 18) ? "Good day." : "Good evening.";
    System.out.println(result);
    ```