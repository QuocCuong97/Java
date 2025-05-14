# JVM Options
Khi nói đến **JVM options**, chúng ta có thể chia chúng thành các nhóm dựa trên mức độ tiêu chuẩn hóa, mục đích sử dụng, và cách chúng tác động đến hoạt động của **Java Virtual Machine (JVM)**.
## **1) Phân loại**
### 1.1) Standard Options

* Đây là nhóm các **options** được định nghĩa rõ ràng trong đặc tả kỹ thuật của **JVM**. Điều này có nghĩa là chúng phải được hỗ trợ bởi bất kỳ **JVM implementation** nào tuân thủ theo đặc tả.
* Chúng thường được sử dụng cho các tác vụ cơ bản và phổ biến.
* Đặc điểm: Không có tiền tố đặc biệt.
* **VD :**
    * `-version`: Hiển thị thông tin phiên bản của **JVM**.
    * `-help` hoặc `-?`: Hiển thị thông tin trợ giúp về cách sử dụng lệnh `java`.
    * `-D<name>=<value>`: Thiết lập một **system property**. Mặc dù về mặt kỹ thuật là một **standard option**, nó thường được coi là một cơ chế để cấu hình ứng dụng hơn là bản thân **JVM**.
### **1.2) Non-Standard Options (X Options)**
- Đây là nhóm các **options** không được định nghĩa trong đặc tả **JVM**. Do đó, việc hỗ trợ chúng có thể khác nhau giữa các **JVM implementations** (VD: **HotSpot**, **J9**, **GraalVM**) và thậm chí giữa các phiên bản khác nhau của cùng một **JVM**.
- Chúng thường được sử dụng để cấu hình các khía cạnh quan trọng nhưng không phải là một phần cốt lõi của đặc tả, chẳng hạn như quản lý bộ nhớ ban đầu và tối đa (**initial heap size** `-Xms`, **maximum heap size** `-Xmx`), kích thước **thread stack** (`-Xss`), và bật/tắt một số tính năng cơ bản.
- Đặc điểm: Bắt đầu bằng tiền tố `-X`.
- **VD :**
    * `-Xms<size>`: Thiết lập **initial heap size**.
    * `-Xmx<size>`: Thiết lập **maximum heap size**.
    * `-Xss<size>`: Thiết lập kích thước **thread stack size**.
    * `-Xint`: Chạy **JVM** ở chế độ interpreted-only (thường dùng cho mục đích debug).
    * `-Xcomp`: Buộc **JVM** biên dịch ahead-of-time (AOT) ngay từ đầu (có thể ảnh hưởng đến thời gian khởi động).
### 1.3) Advanced Options
* Đây là nhóm các **options** không chuẩn và thường liên quan đến các cấu hình rất cụ thể và sâu bên trong **JVM**, chẳng hạn như các thuật toán và tham số của **garbage collection (GC)**, hành vi của **Just-In-Time (JIT) compiler**, quản lý **native memory**, và các hệ thống con runtime khác.
* Chúng thường được coi là "advanced" vì chúng đòi hỏi sự hiểu biết sâu sắc về kiến trúc và hoạt động bên trong của **JVM**. Việc sử dụng sai các **XX options** có thể dẫn đến các vấn đề về hiệu suất và ổn định.
* Sự hỗ trợ và hành vi của các **XX options** có thể thay đổi đáng kể giữa các phiên bản **JVM** và các nhà cung cấp.
* **Đặc điểm:** Bắt đầu bằng tiền tố `-XX:`.
* **Phân loại nhỏ hơn trong nhóm XX Options:**
    * **Boolean Options:** Bật một tính năng bằng cách sử dụng dấu `+` (ví dụ: `-XX:+UseG1GC` để kích hoạt **G1 Garbage Collector**) và tắt bằng dấu `-` (ví dụ: `-XX:-DisableExplicitGC` để vô hiệu hóa lời gọi `System.gc()`).
    * **Value Options:** Nhận một giá trị, thường là số hoặc chuỗi (ví dụ: `-XX:MaxGCPauseMillis=200` để đặt mục tiêu thời gian dừng **GC** tối đa là 200 milliseconds, `-XX:SurvivorRatio=8` để cấu hình tỉ lệ giữa **Eden space** và **Survivor spaces**).
### **1.4) Các Nhóm Liên Quan**
- **System Properties (`-D<name>=<value>`):** Như đã đề cập, đây là cơ chế để truyền các thuộc tính cấu hình cho ứng dụng Java. Chúng có thể ảnh hưởng đến hành vi của các thư viện và framework mà ứng dụng sử dụng.
- **Java Agents (`-javaagent:<path-to-agent>[=<options>]`):** Đây là một cơ chế để load các agent code (thường là các file `.jar`) có thể theo dõi và can thiệp vào hoạt động của **JVM**. Các **Java agents** thường được sử dụng cho profiling, monitoring, debugging, và các mục đích instrumentation khác.

| Loại Option | Tiền tố | Mức độ Tiêu Chuẩn Hóa | Mục Đích Sử Dụng Chính | VD |
| ----------- | ------- | --------------------- | ---------------------- | ----- |
| **Standard Options** | `None` | Được định nghĩa trong đặc tả **JVM** | Các tác vụ cơ bản, thông tin **JVM**, thiết lập **system properties** | `-version`, `-help`, `-Dmyapp.log.level=DEBUG` |
| **Non-Standard (X Options)** | `-X` | Không thuộc đặc tả **JVM** | Cấu hình bộ nhớ cơ bản (**heap**, **stack**), bật/tắt một số tính năng cơ bản | `-Xms1g`, `-Xmx4g`, `-Xss256k`, `-Xint`, `-Xcomp` |
| **Advanced (XX Options)** | `-XX:` | Không thuộc đặc tả **JVM** | Tinh chỉnh **garbage collection**, **JIT compiler**, **native memory**, runtime sâu | `-XX:+UseG1GC`, `-XX:MaxGCPauseMillis=100`, `-XX:SurvivorRatio=6` |
| **System Properties** | `-D` | Standard Option (cơ chế) | Cấu hình ứng dụng Java | `-Djava.awt.headless=true`, `-Dfile.encoding=UTF-8` |
| **Java Agents** | `-javaagent` | Không thuộc core **JVM** | Instrumentation, profiling, monitoring, debugging | `-javaagent:/path/to/my-profiler.jar`, `-javaagent:my-agent.jar=options` |



________
**Refer** :
- https://www.jrebel.com/blog/jvm-options-cheat-sheet
- https://www.oracle.com/java/technologies/javase/vmoptions-jsp.html