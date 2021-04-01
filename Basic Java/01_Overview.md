# Tổng quan về Java
## **1) Giới thiệu**
- Trang chủ: https://www.oracle.com/java/technologies/java-se-glance.html
- Ngôn ngữ **Java** ban đầu được phát triển bởi **Sun Microsystems**, được khởi xướng bởi **James Gosling** và được ra đời năm `1995` như thành phần cốt lõi của nền tảng **Java** của **Sun Microsystems** (**Java 1.0 [J2EE]**).
- Phiên bản mới nhất của **Java Standard Edition** là **Java SE 16** (*March 16, 2021*). Với sự tiến bộ và sự phổ biến rộng rãi của nó, nhiều cấu hình đã được xây dựng phù hợp với nhiều loại nền tảng khác nhau.
- Các phiên bản **J2** mới lần lượt được đổi tên thành
    - **Java SE**
    - **Java EE** (phiên bản ứng dụng doanh nghiệp)
    - **J2ME** (phiển bản cho ứng dụng di động)
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
## **2) Tại sao nên sử dụng Java**
- **Java** hoạt động trên nhiều nền tảng khác nhau (Windows, Mac, Linux, Raspberry Pi,..)
- **Java** là ngôn ngữ phổ biến nhất thế giới
- **Java** rất dễ học và dễ sử dụng
- **Java** là mã nguồn mở và hoàn toàn miễn phí
- **Java** bảo mật, nhanh và mạnh mẽ
- **Java** có cộng đồng support lớn (khoảng 10.000.000 lập trình viên)
- **Java** là một ngôn ngữ hướng đối tượng, đưa đến cấu trúc rõ ràng cho các chương trình, cho phép code được tái sử dụng, giảm chi phí phát triển.
- Vì **Java** cũng gần như **C++** và **C#**, sẽ dễ cho lập trình viên khi chuyển từ **Java** sang các ngôn ngữ khác.
## **3) Cài đặt Java JDK 16**
### **3.1) Cài đặt trên Linux**
#### **3.1.1) Cài đặt trên CentOS/RHEL 7**
- **B1 :** Download gói cài đặt :
    ```
    # wget --no-cookies --no-check-certificate --header "Cookie: gpw_e24=http%3A%2F%2Fwww.oracle.com%2F; oraclelicense=accept-securebackup-cookie" "https://download.oracle.com/otn-pub/java/jdk/16+36/7863447f0ab643c585b9bdebf67c69db/jdk-16_linux-x64_bin.rpm"
    ```
- **B2 :** Cài đặt **JDK 16** vừa download :
    ```
    # rpm -Uvh jdk-16_linux-x64_bin.rpm
    ```
- **B3 :** Kiểm tra lại version :
    ```
    # java --version
    ```
    => Output :
    ```
    java 16 2021-03-16
    Java(TM) SE Runtime Environment (build 16+36-2231)
    Java HotSpot(TM) 64-Bit Server VM (build 16+36-2231, mixed mode, sharing)
    ```
#### **3.1.2) Cài đặt trên Ubuntu 20.04**
- **B1 :** Download gói cài đặt :
    ```
    $ wget --no-cookies --no-check-certificate --header "Cookie: gpw_e24=http%3A%2F%2Fwww.oracle.com%2F; oraclelicense=accept-securebackup-cookie" "https://download.oracle.com/otn-pub/java/jdk/16+36/7863447f0ab643c585b9bdebf67c69db/jdk-16_linux-x64_bin.deb"
    ```
- **B2 :** Cài đặt **JDK 16** vừa download :
    ```
    $ sudo dpkg -i jdk-16_linux-x64_bin.deb
    ```
- **B3 :** Set alternative reference :
    ```
    $ sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/jdk-16/bin/java 100
    ```
- **B3 :** Kiểm tra lại version :
    ```
    $ java --version
    ```
    => Output :
    ```
    java 16 2021-03-16
    Java(TM) SE Runtime Environment (build 16+36-2231)
    Java HotSpot(TM) 64-Bit Server VM (build 16+36-2231, mixed mode, sharing)
    ```
### **3.2) Cài đặt trên Windows**
- **B1 :** Download **Java JDK 16** tại [link](https://download.oracle.com/otn-pub/java/jdk/16+36/7863447f0ab643c585b9bdebf67c69db/jdk-16_windows-x64_bin.exe).
- **B2 :** Chạy file `jdk-16_windows-x64_bin.exe`, chọn ***Next*** :

    <p align=center><img src="https://i.imgur.com/eQKt4Bd.png" width=50%></p>

- **B3 :** Tại cửa sổ **Destination Folder**, chọn ***Next*** để chọn đường dẫn mặc định :

    <p align=center><img src="https://i.imgur.com/9FHTlqg.png" width=50%></p>

- **B4 :** Chọn ***Close*** để hoàn tất quá trình cài đặt :

    <p align=center><img src="https://i.imgur.com/HoFl8CU.png" width=50%></p>

- **B5 :** Truy cập ***Control Panel*** > ***System and Security*** > ***System*** > ***Advanced System Settings*** :

    <p align=center><img src="https://i.imgur.com/UBxLrJD.png" width=70%></p>

- **B6 :** Trong tab **Advanced**, chọn ***Environment Variables...*** :

    <p align=center><img src="https://i.imgur.com/jZH58p8.png" width=50%></p>

- **B7 :** Tại cửa sổ **Environment Variables**, thay đổi **Path** của Windows :

    <p align=center><img src="https://i.imgur.com/PcJhNau.png" width=50%></p>

- **B8 :** Chọn ***New*** để thêm đường dẫn cho **Java** :

    <p align=center><img src="https://i.imgur.com/HMTlLBw.png" width=50%></p>

- **B9 :** Thêm đường dẫn cài đặt **Java** `C:\Program Files\Java\jdk-16\bin`, sau đó chọn ***OK*** để hoàn tất :

    <p align=center><img src="https://i.imgur.com/wlP3gf3.png" width=50%></p>

- **B10 :** Kiểm tra lại version **Java** đã cài đặt :
    ```
    > java --version
    ```
    ```
    java 16 2021-03-16
    Java(TM) SE Runtime Environment (build 16+36-2231)
    Java HotSpot(TM) 64-Bit Server VM (build 16+36-2231, mixed mode, sharing)
    ```

    
    