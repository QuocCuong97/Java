# Cú pháp cơ bản
## **1) Compiler**
- **Compiler** hay còn gọi là ***Trình biên dịch***, là một chương trình có nhiệm vụ dịch các các code của một ngôn ngữ lập trình tương ứng thành một chương trình tương đương của ngôn ngữ cấp thấp hơn (thường là ngôn ngữ máy).
- **Javac** chính là Compiler của java, **Javac** sẽ dịch code Java sang mã bytecode, bytecode chính là vị trí trung gian giữa mã nguồn (ở đây là java) và mã máy (machine code). Thông qua **Java VM** sẽ chuyển bytecode sang mã máy để chạy chương trình.

    <p align=center><img src=https://i.imgur.com/j1IxPky.png width=80%></p>

## **2) Hello-World!**
- Viết 1 đoạn code đầu tiên và lưu thành file `Main.java` :
    ```java
    public class Main {

        public static void main(String[] args) {
            // In "Hello World" trên terminal window.
            System.out.println("Hello World");
        }

    }
    ```
    - Giải thích :
        - Tất cả code chạy trong Java đều được đặt trong một **class**. Trong ví dụ trên, sử dụng class `Main`. Một **class** nên được đặt tên bắt đầu bằng chữ in hoa.
        - Trong **Java** phân biệt chữ hoa chữ thường. `MyClass` và `myclass` sẽ khác nhau.
        - Tên của file java phải trùng với tên class. Khi lưu file, sử dụng tên class và thêm đuôi "`.java`" vào cuối.
- Gõ lệnh sau để biên dịch code java sang bytecode. Sau khi chạy lệnh trên thì compiler sẽ tạo ra file `main.class` chính là file lưu bytecode của class `Main` của đoạn code trên.
    ```
    C:\Java> javac Main.java
    ```
- Bây giờ để máy tính có thể chạy chương trình Java, sử dụng lệnh sau để thực thi bytecode sang mã máy rồi chạy chương trình :
    ```
    C:\Java> java Main
    Hello World
    ```
    - Đây chính là kết quả in ra màn hình của lệnh `System.out.println()`.
## **3) Comment trong Java**
- **Comment** có thể được sử dụng để giải thích cho các đoạn Java code, để khiến chúng dễ hiểu hơn. Chúng cũng có thể được sử dụng để chặn thực thi dòng code khi đang thực hiện test.
- **Single-line comment** bắt đầu bằng dấu `//`. Bắt cứ đoạn text nào xuất hiện sau dấu `//` đến hết dòng sẽ không được thực thi.
- **VD1 :**
    ```java
    // This is a comment
    System.out.println("Hello World");

    System.out.println("Hello World"); // This is a comment
    ```
- **Multi-line comment** bắt đầu bằng dấu `/*` và kết thúc bằng dấu `*/` . Bất cứ đoạn text nào ở giữa khoảng 2 dấu này sẽ được **Java** bỏ qua không thực thi.
- **VD2 :**
    ```java
    /* The code below will print the words Hello World
    to the screen, and it is amazing */
    System.out.println("Hello World");
    ```