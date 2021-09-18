# String trong Java
- **String** được sử dụng để lưu trữ text.
- Biến `String` bao gồm một tập hợp các ký tự bao quanh bởi dấu `" "`.
    ```java
    String greeting = "Hello";
    ```
### **String Length**
- **String** trong **Java** là một object, vì vậy có các phương thức để áp dụng trên nó. Ví dụ, chiều dài của string có thể tính ra qua phương thức `length()` :
    ```java
    String txt = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
    System.out.println("The length of the txt string is: " + txt.length());
    ```
    - Output : `The length of the txt string is: 26`
### **Các phương thức khác**
- Có nhiều phương thức string, ví dụ như `toUpperCase()` để convert thành chữ hoa hoặc `toLowerCase()` để convert thành chữ thường.
    ```java
    String txt = "Hello World";
    System.out.println(txt.toUpperCase());   // Outputs "HELLO WORLD"
    System.out.println(txt.toLowerCase());   // Outputs "hello world"
    ```
    - Output :
        ```
        HELLO WORLD
        hello world
        ```
### **Tìm ký tự trong String**
- Phương thức `indexOf` trả về index (vị trí) của chữ cái đầu tiên trong đoạn text chỉ định trong string (bao gồm cả whitespace). Index sẽ bắt đầu từ `0` :
    ```java
    String txt = "Please locate where 'locate' occurs!";
    System.out.println(txt.indexOf("locate")); // Outputs 7
    ```
    - Output : `7`
### **Gộp string**
- Toán tử `+`có thể được sử dụng kể kết hợp các string với nhau (***string concatenation***) :
    ```java
    String firstName = "John";
    String lastName = "Doe";
    System.out.println(firstName + " " + lastName);
    ```
    - Output : `John Doe`
- Cũng có thể sử dụng phương thức `concat()` để gộp string :
    ```java
    String firstName = "John ";
    String lastName = "Doe";
    System.out.println(firstName.concat(lastName));
    ```
    - Output : `Jonh Doe`
### Các ký tự đặt biệt
- Vì string được đặt trong cặp dấu `" "`, **Java** sẽ không hiểu được những trường hợp đặc biệt, đôi khi gây ra lỗi :
    ```java
    String txt = "We are the so-called "Vikings" from the north.";
    ```
- Giải pháp để tránh được các vấn đề đó là sử dụng ***backslash escape character*** :
    
    | Escape character | Kết quả | Mô tả |
    |------------------|---------|-------|
    | `\'` | `'` | Dấu nháy đơn |
    | `\"` | `"` | Dấu nháy đôi |
    | `\\` | `\` | Dấu sược |

- **VD1 :** Sử dụng dấu `\"` trong string :
    ```java
    String txt = "We are the so-called \"Vikings\" from the north.";
    ```
    - Output : `We are the so-called "Vikings" from the north.`
- **VD2 :** Sử dụng dấu `\'` trong string :
    ```java
    String txt = "It\'s alright.";
    ```
    - Output : `It's alright.`
- **VD3 :** Sử dụng dấu `\\` trong string :
    ```java
    String txt = "The character \\ is called backslash.";
    ```
- Các ***escape character*** trong **Java** :

    | Escape character | Kết quả |
    |------------------|---------|
    | `\n` | New Line |
    | `\r` | Carriage Return |
    | `\t` | Tab |
    | `\b` | Backspace |
    | `\f` | Form Feed |

### **Kết hợp Number và String**
- Khi cộng 2 số, kết quả sẽ là 1 số :
    ```java
    int x = 10;
    int y = 20;
    int z = x + y;   // z will be 30 (an integer/number)
    ```
- Khi cộng 2 string, kết quả sẽ là 1 string :
    ```java
    String x = "10";
    String y = "20";
    String z = x + y;   // z will be 1020 (a String)
    ```
- Khi cộng số và string, kết quả sẽ là 1 string :
    ```java
    String x = "10";
    int y = 20;
    String z = x + y;   // z will be 1020 (a String)
    ```