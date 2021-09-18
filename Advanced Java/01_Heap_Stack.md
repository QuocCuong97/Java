# Phân biệt Heap memory và Stack memory trong Java
## **1) Giới thiệu**
- Việc **Quản lý bộ nhớ** đối với một lập trình viên là rất quan trọng.
- Mục đích quan trọng của việc quản lý bộ nhớ là cung cấp những cách thức để cấp phát động các ô nhớ cho chương trình khi được yêu cầu và giải phóng các ô nhớ đó khi không cần dùng nữa. Đây là việc rất quan trọng đối với bất kỳ hệ thống máy tính cao cấp nào vì sẽ có nhiều công việc được tiến hành ở mọi thời điểm.
- Nhiều phương pháp đã được tìm ra để gia tăng hiệu quả của việc quản lý bộ nhớ. Những hệ thống bộ nhớ ảo giúp tách những địa chỉ ô nhớ đang được dùng ra khỏi những địa chỉ thực, từ đó cho phép chia sẻ công việc và gia tăng lượng RAM một cách hiệu quả nhờ đánh dấu địa chỉ hoặc chuyển đến vùng lưu trữ thứ hai. Chất lượng của việc quản lý bộ nhớ ảo có thể có tác dụng lớn đến hiệu năng làm việc của hệ thống nói chung.
## **2) Stack và Heap memory**
- **Heap memory** và bộ nhớ **Stack memory** bản chất đều cùng là vùng nhớ được tạo ra và lưu trữ trong RAM khi chương trình được thực thi.
- **Stack memory** được dùng để lưu trữ các biến cục bộ trong hàm, tham số truyền vào... Truy cập vào bộ nhớ này rất nhanh và được thực thi khi chương trình được biên dịch.
- **Heap memory** được dùng để lưu trữ vùng nhớ cho những biến con trỏ được cấp phát động bởi các hàm  hoặc từ khóa `new`.
- **VD :**
    ```java
    public void Method1() {
        int i = 4;
        int y = 2;
        class1 cls1 = new class1();
    }
    ```
    - Trong đó :
        - Khi khai báo int `i = 4` nó sẽ đưa `i = 4` vào **stack**
        - Khi khai báo `y = 2` nó sẽ đưa `y = 2` vào **stack** (xếp trên `i = 4`)
        - Khi khai báo `class1 cls1 = new class1()`: đây là kiểu đối tượng nên nó sẽ tạo đối tượng `cls1` trong **heap** đồng thời chưa tham chiếu của đối tượng `cls1` vào **stack** (xếp trên cùng trong **stack**)
        - Sau khi kết thúc method, bộ nhớ trong **stack** được giải phóng, còn bộ nhớ trong **heap** thì chưa. Bộ nhớ trong **heap** phải chờ cho tới khi **garbage collector** (bộ dọn rác) của **Java** quét qua để giải phóng.
- Kích thước vùng nhớ
    - **Stack memory** : kích thước của **Stack memory** là cố định, tùy thuộc vào từng hệ điều hành, ví dụ hệ điều hành Windows là `1 MB`, hệ điều hành Linux là `8 MB` (lưu ý là con số có thể khác tùy thuộc vào kiến trúc hệ điều hành).
    - **Heap memory** : kích thước của bộ nhớ **Heap memory** là không cố định, có thể tăng giảm do đó đáp ứng được nhu cầu lưu trữ dữ liệu của chương trình.
- Đặc điểm vùng nhớ :
    - **Stack memory** : **Stack memory** được quản lý bởi hệ điều hành, dữ liệu được lưu trong **Stack memory** sẽ tự động hủy khi hàm thực hiện xong công việc của mình.
    - **Heap memory** : **Heap memory** được quản lý bởi lập trình viên, dữ liệu trong **Heap memory** sẽ không bị hủy khi hàm thực hiện xong, điều đó có nghĩa bạn phải tự tay hủy vùng nhớ bằng câu lệnh `free` (trong `C`), và delete hoặc `delete []` (trong `C++`), nếu không sẽ xảy ra hiện tượng rò rỉ bộ nhớ. Ở các ngôn ngữ lập trình bậc cao như .NET, Java, ... đã có chế dọn rác tự động (**Garbage Collection**), không cần phải tự tay hủy vùng nhớ **Heap memory** nữa.
## **3) Vấn đề lỗi xảy ra đối với vùng nhớ**
- **Stack memory** : bởi vì **Stack memory** cố định nên nếu chương trình bạn sử dụng quá nhiều bộ nhớ vượt quá khả năng lưu trữ của Stack chắc chắn sẽ xảy ra tình trạng tràn **Stack memory** (***Stack overflow***), các trường hợp xảy ra như bạn khởi tạo quá nhiều biến cục bộ, hàm đệ quy vô hạn,...
    - Ví dụ về tràn **Stack memory** với hàm đệ quy vô hạn :
        ```java
        int foo(int x){
            printf("De quy khong gioi han\n");
            return foo(x);
        }
        ```
- **Heap memory** : Nếu bạn liên tục cấp phát vùng nhớ mà không giải phóng thì sẽ bị lỗi tràn **Heap memory** (***Heap overflow***). Nếu khởi tạo một vùng nhớ quá lớn mà **Heap memory** không thể lưu trữ một lần được sẽ bị lỗi khởi tạo **Heap memory** thất bại.
    - Ví dụ trường hợp khởi tạo **Heap memory** quá lớn:
        ```java
        int *A = (int *)malloc(18446744073709551615);
        ```
## **4) Khi nào nên sử dụng bộ nhớ Heap và bộ nhớ Stack?**
- Sử dụng **Stack memory** nếu bạn biết chính xác lượng dữ liệu mà bạn phân bổ trước khi biên dịch và dữ liệu không quá lớn. Ngược lại, bạn nên sử dụng Heap...
- Trong các ứng dụng đa luồng chạy song song (multithreading), mỗi luồng xử lý (thread) sẽ có **Stack memory** riêng của nó, trong khi tất cả các luồng cùng chia sẻ một **Heap memory**. Sử dụng chung vùng nhớ **Heap memory** đồng nghĩa với việc phải đồng bộ hóa để tránh tình trạng xảy ra mâu thuẫn giữa các luồng, cho nên cấp phát **Heap memory** phải cài đặt thêm một số cơ chế do đó thực hiện lâu hơn so với cấp phát **Stack memory**. Cấp phát và hủy **Heap memory** liên tục có thể xảy ra tình trạng phân mảnh bộ nhớ, từ phân mảnh bộ nhớ có thể dẫn đến lỗi cấp phát bộ nhớ thất bại như những mô tả ở trên.