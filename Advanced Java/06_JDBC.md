# JDBC
## **1) Giới thiệu**
- **JDBC** - **Java Database Connectivity** là một API dùng để kết nối và thực thi các câu lệnh SQL xuống database.
- **JDBC API** sử dụng **JDBC driver** để làm việc với database gồm 4 loại :
    - JDBC-ODBC Bridge Driver
    - Native Driver
    - Network Protocol Driver
    - Thin Driver
- Kiến trúc của JDBC gồm 2 tầng:
    - JDBC API – cho phép ứng dụng kết nối đến JDBC Manager connection. JDBC API cung cấp cơ chế kết nối đến đến các loại database khác nhau theo một chuẩn đồng nhất.
    - JDBC Driver API: Hỗ trợ JDBC Manager đến Driver connection. JDBC driver đảm bảo cho JDBC API kết nối đến database mà nó cần. Đối với mỗi database sẽ có JDBC driver riêng mà JDBC API có thể chỉ định để làm việc với nó.

    <p align=center><img src=https://i.imgur.com/aTsNbyh.png width=50%></p>

## **2) Các thành phần chính trong JDBC**
- JDBC API cung cấp một số class và interface:
    - DriverManager – class này chịu trách nhiệm quản lý danh sách các database driver, và chịu trách nhiệm tạo kết nối tương ứng đến database cụ thể được chỉ định. Driver
    - Interface chịu trách nhiệm xử lý các hoạt động giao tiếp giữa ứng dụng với database. 
    - Connection – Interface cung cấp tất cả các hàm cho việc thao tác với database.
    - Statement – dùng các object được tạo ra từ interface này để thực thi các câu lệnh SQL xuống database. 
    - ResultSet: Lưu trữ kết quả trả về từ database. 
    - SQLException – Xử lý các lỗi xảy ra trong database.
## **3) Nguyên tắc kết nối của JDBC**
- Java sử dụng JDBC để làm việc với các cơ sở dữ liệu.

    <p align=center><img src=https://i.imgur.com/Nk4mmRP.png></p>

- **VD :** làm việc với cơ sở dữ liệu Oracle từ Java bạn cần phải có Driver (Đó là class điều khiển việc kết nối với loại cơ sở dữ liệu bạn muốn). Trong JDBC API chúng ta có `java.sql.Driver`, nó chỉ là một interface, và nó có sẵn trong JDK. Như vậy bạn phải download thư viện Driver ứng với loại Database mà bạn mong muốn. 
    - Chẳng hạn với Oracle thì class thi hành Interface `java.sql.Driver` đó là: `oracle.jdbc.driver.OracleDriver`
    - `java.sql.DriverManager` là một class trong JDBC API. Nó làm nhiệm vụ quản lý các Driver.

    <p align=center><img src=https://i.imgur.com/HksUsgH.png width=80%></p>
- Có 2 cách để làm việc với một loại cơ sở dữ liệu cụ thể nào đó.
    - **Cách 1:** Bạn hãy cung cấp thư viện Driver điều khiển loại cơ sở dữ liệu đó, đây là cách trực tiếp. Nếu bạn dùng DB oracle (hoặc DB khác) bạn phải download thư viện dành cho loại DB này.
    - **Cách 2:** Khai báo một "ODBC DataSource", và sử dụng cầu nối JDBC-ODBC để kết nối với "ODBC DataSource" kia. Cầu nối JDBC-ODBC là thứ có sẵn trong JDBC API.
        - ODBC - Open Database Connectivity: Nó chính là một bộ thư viện mở, có khả năng kết nối với hầu hết các loại cơ sở dữ liệu khác nhau, và nó miễn phí. Được cung cấp bởi Microsoft.
        - ODBC DataSource: Trên hệ điều hành Window bạn có thể khai báo một kết nối ODBC tới một loại DB nào đó. Và như vậy chúng ta có một nguồn dữ liệu (Data Source).
        - Trong JDBC API, đã xây dựng sẵn một cầu nối JDBC-ODBC để JDBC có thể nói chuyện được với ODBC Data Source.
    > Về tốc độ, cách 1 sẽ nhanh hơn cách 2, vì cách 2 phải sử dụng tới cầu nối.