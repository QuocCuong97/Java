# Tổng quan về JVM
## **1) Giới thiệu**
- Các thành phần trong **Java** :

    <img src=https://i.imgur.com/sKuUnyF.png>

- Máy ảo Java (JVM - Java Virtual Machine) dùng để thực thi chương trình Java. Mỗi nền tảng sẽ có một JVM tương ứng có cơ chế hoạt động giống nhau, nên các chương trình chạy giống nhau trên bất kỳ nền tảng nào có hỗ trợ **JVM**.
- **JVM** có 3 thành phần chính : Class Loader, Runtime Data Area, Execution Engine :

    <p align=center><img src=https://i.imgur.com/3xlGfzB.png width=70%></p>

- Các loại vùng nhớ trong **JVM** :
    - Method Area : lưu trữ dữ liệu class như tên class, tên parent class trực tiếp, các method, các thuộc tính (bao gồm cả thuộc tính tĩnh) và source code của các method. Mỗi **JVM** chỉ có một Method Area dùng chung cho tất cả các thread.
    - Heap Area : lưu trữ các object kiểu string, array, thể hiện của các class (được tạo ra bằng từ khóa `New`). Mỗi **JVM** được cấp một Heap Area, dùng chung cho tất cả các thread.
    - Stack Area : lưu trữ các biến local, mỗi tiến trình thread có một stack memory riêng. Trong stack chứa nhiều frame, mỗi frame sẽ được tạo khi function/method được gọi để lưu trữ các biến local, và các parameter truyền vào cho nó. Frame sẽ bị hủy khi function call/method kết thúc.
    - PC Register (Program Counter) : thanh ghi lưu địa chỉ lệnh đang thực thi, mỗi thread có một PC riêng.
    - Native Method Stacks : chứa các hàm hệ thống dùng trong chương trình, mỗi thread có Native Method Stack riêng
## **2) Quản lý bộ nhớ trong Java**
- Khi chương trình bắt đầu, JVM sẽ yêu cầu HĐH cung cấp bộ nhớ trên RAM để chương trình hoạt động.
- JVM chia bộ nhớ được cấp phát thành 2 phần : Heap memory và Stack memory.
### **2.1) Heap memory**
- Bộ nhớ này được sử dụng để lưu các đối tượng được tạo ra khi chương trình thực thi (runtime).
- Dung lượng của bộ nhớ này phụ thuộc kích thước và số lượng các object được tạo trong quá trình thực thi chương trình.
- Khi Heap memory không đủ để cấp phát cho object, sẽ gây ra exception `java.lang.OutOfMemoryError`.
- Lifetime của object trên Heap phụ thuộc hoạt động của bộ thu gom rác - **Garbage Collector**.
- **Garbage Collector** chạy trên Heap memory và sẽ tự động xóa các object khi trong chương trình không còn biến nào tham chiếu đến nó nữa.
### **2.2) Stack memory**
- Bộ nhớ này thường có dung lương nhỏ, dùng để lưu trữ các biến local bao gồm các biến có kiểu dữ liệu cơ bản, các biến tham chiếu đến object trên Heap memory, các parameter được truyền vào function.
- Bộ nhớ này hoạt động theo cơ chế LIFO (Last-In-First-Out) có nghĩa là biến được tạo sau sẽ bị hủy trước.
- Nếu Stack memory không đủ để cấp phát cho biến local thì sẽ gây ra exception `java.lang.StackOverFlowError`.
- Khi một method được gọi, một khối memory trên Stack sẽ được cấp phát cho nó để lưu các biến local và khối memory này sẽ được giải phóng khi method đã thực hiện xong.
### **2.3) Garbage Collector**
- Garbage Collector là bộ thu gom rác trong JVM, nó tự động hủy các object không còn sử dụng (không có tham chiếu nào đến nó) trong Heap memory và không gian này có thể dùng cấp phát cho các object khác.
- Tham chiếu đến một object có thể bị hủy trong các trường hợp sau :
    - Biến tham chiếu khai báo local hết phạm vi hoạt động.
    - Biến tham chiếu đến object khác.
    - Biến được gán giá trị `null`.
- Có 2 cách để chủ động sử dụng **Garbage Collection** trong **JVM** là :
    - Sử dụng phương thức `System.gc()`
    - Sử dụng phương thức `Runtime.getRuntime().gc()`
> Tìm hiểu thêm về Long GC : https://stackoverflow.com/questions/55938677/how-to-deal-with-long-full-garbage-collection-cycle-in-java