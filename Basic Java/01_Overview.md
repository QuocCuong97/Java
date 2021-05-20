# Tổng quan về Java
## **1) Giới thiệu**
- Trang chủ: https://www.oracle.com/java/technologies/java-se-glance.html
- Ngôn ngữ **Java** ban đầu được phát triển bởi **Sun Microsystems**, được khởi xướng bởi **James Gosling** và được ra đời năm `1995` như thành phần cốt lõi của nền tảng **Java** của **Sun Microsystems** (**Java 1.0 [J2EE]**).
- Phiên bản mới nhất của **Java Standard Edition** là **Java SE 16** (*March 16, 2021*). Với sự tiến bộ và sự phổ biến rộng rãi của nó, nhiều cấu hình đã được xây dựng phù hợp với nhiều loại nền tảng khác nhau.
- Các phiên bản **J2** mới lần lượt được đổi tên thành
    - **Java SE**
    - **Java EE** (phiên bản ứng dụng doanh nghiệp)
    - **J2ME** (phiên bản cho ứng dụng di động)
- **Java** được đảm bảo có thể "***Write Once, Run Anywhere***"
- **Java** hiện được sở hữu bởi **Oracle**, với hơn 3 tỷ thiết bị trên thế giới chạy **Java**.
- **Java** được sử dụng cho mục đích:
    - Mobile application (đặc biệt là Android apps)
    - Desktop applications
    - Web applications
    - Web server và Application servers
    - Game
    - Database connection
    - .........
## **2) Đặc trưng cơ bản và điểm nổi bật của Java**
### **2.1) Đặc trưng cơ bản**
- Là ngôn ngữ hướng đối tượng
- Chạy bằng máy ảo **Java**. Chương trình muốn thực thi phải biên dịch ra mã máy, mà mã máy mỗi hệ điều hành là khác nhau như Windows biên dịch dưới dạng file có đuôi `.exe` còn Linux có dạng đuôi `.elf`. Việc **Java** có thể chạy mọi hệ điều hành là do nhà phát triển Sun Microsytems phát triển máy ảo (**JVM**) chịu trách nhiệm việc này.

    <p align=center><img src=https://i.imgur.com/Kgo0Z4Y.png width=60%></p>

- Đa nhiệm – Đa luồng: Java hỗ trợ lập trình đa nhiệm, đa luồng cho phép chạy nhiều tiến trình chạy song song trong một thời điểm và tương tác lẫn nhau.
- Java bỏ đa kế thừa trong C++ thay bằng sử dụng Interface
### **2.2) Các điểm nổi bật**
- **Java** là mã nguồn mở và hoàn toàn miễn phí
- **Java** là ngôn ngữ phổ biến nhất thế giới
- **Java** có cộng đồng support lớn (khoảng 10.000.000 lập trình viên)
- Độc lập phần cứng và hệ điều hành: **Java** được thiết kế để biên dịch code thành bytecode và bytecode sẽ chạy trên môi trường thực thi. Nên chương trình **Java** có thể chạy trên nhiều thiết bị, nhiều hệ điều hành khác nhau.

    <p align=center><img src=https://i.imgur.com/zL8Cdrz.png width=60%></p>

- Mạnh mẽ: quá trình cấp phát, giải phóng bộ nhớ thực hiện tự động. Không sử dụng con trỏ hoặc phép toán con trỏ.
- Bảo mật: Do Java phải biên dịch qua máy ảo Java (JVM) nên sẽ được bảo mật cao hơn khi mọi đối tượng phải qua JVM mới đến hệ điều hành.

    <p align=center><img src=https://i.imgur.com/JwbGPcb.png width=60%></p>

- Phân tán: Java hỗ trợ lập trình cho hệ thống phân tán như client-server, RMI… bằng Java Web, UDP, TCP
## **3) Phân biệt JDK, JRE và JVM**
- **JVM (Java Virtual Machine)** là môi trường dùng để chạy ứng dụng được viết bằng ngôn ngữ lập trình **Java**. **JVM** giúp **Java** có thể chạy nhiều nền tảng (Platform) khác nhau, mỗi nền tảng sẽ có Platform tương ứng như **JVM** giành cho Linux, Mac, Window… nhưng cơ chế hoạt động đều như nhau nên khi ta viết ứng dụng **Java** trên Window vẫn có thể chạy được trên Linux, Mac và ngược lại.
- **JRE (Java Runtime Enviroment)** bao gồm các thư viện, **JVM** và những thành phần bổ sung để chạy những ứng dụng được viết bằng Java. Những máy tính của người dùng bình thường chỉ cần cài đặt **JRE** là đủ chạy ứng dụng Java Desktop (được viết từ những thư viện AWT, Swing hay JavaFX).
- **JDK (Java Development Kit)** giành cho các lập trình viên **Java** là tập hợp **JRE** và những công cụ cần thiết để phát triển ứng dụng bằng **Java**. Ví dụ như trình biên dịch `javac` dùng để biên dịch java thành file bytecode `.class` .

    <p align=center><img src=https://i.imgur.com/VWN5xA3.png width=80%></p>
    
    
    