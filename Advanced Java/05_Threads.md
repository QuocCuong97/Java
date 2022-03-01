# Threads trong Java
## **1) So sánh Thread và Process**

| | Process | Thread |
|-|---------|--------|
| Khái niệm | Một chương trình đang chạy được gọi là một process. | Một chương trình chạy có thể có nhiều thread, Cho phép chương trình đó chạy trên nhiều luồng một cách "đồng thời". |
| Không gian địa chỉ | Mỗi process có một không gian địa chỉ riêng biệt. | Tất cả thread thuộc một process chia sẻ không gian địa chỉ với nhau, hợp chúng lại thành một tiến trình. |
| Đa nhiệm | Đa nhiệm dựa trên process cho phép máy tính chạy 2 hoặc nhiều hơn 2 chương trình đồng thời. | Đa nhiệm dựa trên thread cho phép một chương trình chạy trên 2 hoặc nhiều luồng đồng thời. |
| Giao tiếp | Giao tiếp giữa 2 tiến trình là tốn kém và bị giới hạn. | Giao tiếp giữa 2 thread ít tốn kém hơn so với tiến trình. |
| Thành phần | Một tiến trình có: không gian địa chỉ, biến global, xử lí tín hiệu, những tiến trình con, thông tin tính toán. | Một thread có: thanh ghi, trạng thái, stack, bộ đếm chương trình. |
| Điều khiển | Đa nhiệm dựa trên process không thuộc quyền kiểm soát của Java. | Đa nhiệm dựa trên thread phụ thuộc quyền kiểm soát của Java. |

## **2) Concurrency vs Parallelism**
- Trong multi-threading có tồn tại 2 khái niệm là Concurrency (đồng thời) và Parallelism (song song). Thoạt đầu thì nghĩ chúng có vẻ giống nhau, nhưng chúng không phải là một.
- Concurrency nghĩa là những tác vụ có thể bắt đầu, chạy, và hoàn thành trong những khoảng thời gian chống chéo lên nhau mà không theo thứ tự nào cả. Ví dụ: chạy trên 1 core processor. Còn Parallelism là nhiều tác vụ hoặc một phần của tác vụ chạy đồng thời tại cùng một thời điểm. Ví dụ: chạy trên multi-core processors.
- Concurrency thực sự được ứng dụng khi chúng ta có ít nhất 2 tác vụ trở lên. Khi mà ứng dụng có thể thực hiện 2 task gần như cùng một thời điểm, chúng ta gọi đây là Concurent Application. Có thể chúng ta nhìn thấy nó gần như là thực hiện cùng 1 thời gian nhưng có vẻ không phải như vậy. Chúng tận dụng lợi thế của CPU time-slicing (Chia cắt thời gian) của hệ điều hành, mỗi tác vụ thực hiện nhiệm vụ của nó và chuyển sang trạng thái chờ. Khi tác vụ đầu tiên ở trạng thái chờ, CPU được gán cho tác vụ thứ 2 thực hiện nhiệm vụ của nó. Hệ điều hành dựa trên độ ưu tiên cũng từn task, sẽ phân chia CPU và tài nguyên để tính toán. Đối với người sử dụng, thấy dường như là các task được chạy một cách song song.
- Parallelism không yêu cầu 2 task trở lên để tồn tại. Nó chạy một phần của task hoặc multi-task tại cùng 1 thời gian, dựa vào cấu trúc mult-core của CPU, bằng cách phân chia mỗi core của CPU thực hiện 1 task hoặc 1 sub-task. Parallelism yêu cầu phần cứng phải có nhiều đơn vị xử lí. Đối với CPU có 1 core, bạn có thể thực hiện Concurrency nhưng không thể là Parallelism.
## **3) Thread Pool**
- Để dễ hình dung, chúng ta hãy thử hóa thân thành ban tổ chức của 1 cái giải bơi lội cấp xã. Giả sử có 4 đội bơi tham gia tranh giải, và mỗi đội gồm có 5 vận động viên. Kết quả thi sẽ được tính bằng tổng thời gian bơi của tất cả các thành viên trong đội gộp lại. Bài toán đặt ra là chúng ta sẽ bố trí thể thức giải đấu như nào cho phù hợp?
    - Giải pháp 1: Phân làn bể bơi làm 20 làn tương ứng với 20 bộ bấm giờ cho mỗi vận động viên. Cả 20 người thi cùng 1 lượt.
    - Giải pháp 2: Phân làn bể bơi làm 4 làn và 4 bộ bấm giờ cho mỗi đội. Mỗi đội luân phiên bơi 4 người 1 lượt chia ra làm 5 lượt cả thảy.
- Nhưng 1 chiếc bể vốn chỉ có dung tích giới hạn, việc phân quá nhiều làn sẽ khiến cho lưu thông mỗi làn bị tắc nghẽn. Giả sử tình huống số vận động viên tăng lên đáng kể, vấn đề sẽ càng trở nên nghiêm trọng hơn khi chả ai có khả năng bơi được vì làn bơi quá hẹp. Vậy nên giải pháp 2, tự đặt ra cố định chỉ phân ra làm 4 làn nghe hợp lí 1 cách rõ rệt, và giả như số lượng vận động viên có tăng lên, cũng chỉ khiến cho thời gian tính kết quả lâu hơn mà không khiến giải đấu trở nên nghẽn toàn bộ.
- Java cho phép chúng ta thay vì phải tạo mới Thread cho mỗi task (mỗi vđv 1 làn bơi), thì các task đó được đưa vào trong một ThreadPool với một số lượng Thread cố định (1 bể bơi với số làn cố định). Khi có bất cứ 1Thread nào đang ở trạng thái rảnh rỗi trong pool, nó sẽ được lấy ra để gán với 1 task đang ở trạng thái chờ (khi làn bơi của đội đã có thành viên thi đấu xong, thì thành viên tiếp theo sẽ bắt đầu cuộc thi của mình tại chính làn đó). Điều này sẽ giúp khắc phục được sự tắc nghẽn và chương trình sẽ kiểm soát được các luồng thực thi. Vì mỗi khi có một Thread mới được tạo ra và được cấp phát bộ nhớ bằng từ hóa new thì sẽ có vấn đề bộ nhớ và hiệu suất, có thể dẫn tới crash chương trình.
## **4) Thread lifecycle**

<p align=center><img src=https://i.imgur.com/L9LVrAB.png width=50%></p>


- `Thread.State.NEW` : Đây là trạng thái khi luồng vừa được khởi tạo bằng phương thức khởi tạo của lớp Thread nhưng chưa được start(). Ở trạng thái này, luồng được tạo ra nhưng chưa được cấp phát tài nguyên và cũng chưa chạy. Nếu luồng đang ở trạng thái này mà ta gọi các phương thức ép buộc stop,resume,suspend … sẽ là nguyên nhân sảy ra ngoại lệ IllegalThreadStateException .
- `Thread.State.RUNNABLE` : Sau khi gọi phương thức start() thì luồng test đã được cấp phát tài nguyên và các lịch điều phối CPU cho luồng test cũng bắt đầu có hiệu lực. Ở đây, chúng ta dùng trạng thái là Runnable chứ không phải Running, vì như đã nói ở phần đầu (Các mô hình đa luồng) thì luồng không thực sự luôn chạy mà tùy vào hệ thống mà có sự điều phối CPU khác nhau.
- `Thread.State.BLOCKED` : Đây là 1 dạng của trạng thái “Not Runnable”. Thread chờ 1 đối tượng bị lock bởi JVM Monitor
- `Thread.State.WAITING` : Đây là 1 dạng của trạng thái “Not Runnable”. Thread đang chờ 1 notify() từ 1 thread khác. Thread rơi vào trạng thái này do phương thức wait() hoặc join()
- `Thread.State.TIMED_WAITING` : Đây là 1 dạng của trạng thái “Not Runnable”. Thread đang chờ 1 notify() từ 1 thread khác trong 1 thời gian nhất định, Thread rơi vào trạng thái này do phương thức wait(long timeout) hoặc join(long timeout)
- `Thread.State.TERMINATED` : Thread đã hoàn thành công việc trong run() hoặc bị stop()

> Tham khảo thêm: https://viblo.asia/p/tan-man-ve-thread-trong-java-V3m5WJPblO7