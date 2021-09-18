# Switch
- Mệnh đề `switch` được sử dụng để chọn 1 trong các block code sẽ được thực thi
- Cú pháp :
    ```java
    switch(expression) {
        case x:
            // code block
            break;
        case y:
            // code block
            break;
        default:
            // code block
    }
    ```
- Cách hoạt động :
    - Mệnh đề `switch` sẽ thực hiện đánh giá điều kiện
    - Giá trị của mệnh đề được so sánh với giá trị của mỗi `case`
    - Nếu có sự trùng khớp, block code liên quan sẽ được thực thi
    - 