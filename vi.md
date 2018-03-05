# Hướng dẫn dự án
## 5.Testing  
![Testing](https://github.com/wearehive/project-guidelines/raw/master/images/testing.png)  
 * Có một môi trường `test` nếu cần thiết  
     _Tại sao_:  
    > Đôi khi end testing end trong chế độ `production` có vè như là đủ, có một số ngoại lệ: một ví dụ là bạn có thể không 
    muốn cho phép thông tin phân tích trên chế độ 'production' và làm bẩn bảng điều khiển của ai đó với dữ liệu kiểm thử.
    Một ví dụ khác là API của bạn có thể có giới hạn đánh giá trong `production` và khóa những lời gọi kiểm thử của bạn sau
    lượng yêu cầu nhất định.
 * Đặt các file tets của bạn kế cạnh các modul kiểm thử, sử dụng quy tắc đặt tên `*test.js` hoặc `*spec.js`, như là 
 `moduleName.spec.js`
    _Tại sao_:
    > Bạn không hề muốn đào xuyên qua cấu trúc thư mục để tìm kiếm đơn vị kiểm thử. [đọc thêm](https://hackernoon.com/structure-your-javascript-code-for-testability-9bc93d9c72dc)  
 * Đặt các file test bổ sung vào các thư mục kiểm thử tiêng biệt để tránh sự nhầm lẫn  
    _Tại sao_:
    > Có những file kiểm thử không có liên hệ đầy đủ tới bất kì file thực thi cụ thể nào. Bạn phải đặt nó trong một thư 
    mục mà có khả năng tìm thấy nhất bởi những nhà phát triển khác: thư mục `_test_`. cái tên này: `_test_` cũng là tiêu 
    chuẩn hiện tại và được chọn bởi phần lớn những JavaScript testing frameworks.  
 * Viết mã nguồn kiểm thử được, tránh các hiệu ứng đi kèm, trích xuất các hiệu ứng đi kèm, viết các hàm thuần khiết  
    _Tại sao_:
    > Bạn muốn kiểm tra tư duy kinh doanh như là các đơn vị tách rời. Bạn phải "giảm thiểu các va chạm của những quy trình
     ngẫu nhiên và không xác đinh trên độ tin cậy trong mã nguồn của bạn". [đọc thêm](https://medium.com/javascript-scene/tdd-the-rite-way-53c9b46f45e3)  
     
    > Hàm thuần khiết là hàm mà thường trả về đầu ra tương ứng với đầu vào. Ngược lại, hàm không thuần khiết là một hàm 
    có thể có các hiệu ứng đi kèm hoặc phụ thuộc vào các điều kiện bên ngoài để tạo ra các giá trị. Điều này khiến nó khó 
    dự đoán. [đọc thêm](https://hackernoon.com/structure-your-javascript-code-for-testability-9bc93d9c72dc)  
 * Sử dụng bộ kiểm tra kiểu tĩnh
    _Tại sao_:
    > Đôi khi bạn có thể cần bộ kiểm tra kiểu tĩnh. Nó mang lại những mức độ tin cậy nhất định cho mã nguồn của bạn. [đọc thêm](https://medium.freecodecamp.org/why-use-static-types-in-javascript-part-1-8382da1e0adb)  
 * Tiến hành các kiểm thử cục bộ trước khi tạo bất kì pull request nào tới nhánh `develop`  
    _Tại sao_:
    > Bạn không muốn một người nào đó là nguyên nhân khiến nhánh đã sẵn sàng sản xuất của bạn bị lỗi. Chạy kiểm thử của 
    bạn sau `rebase` của bạn hoặc trước khi đẩy nhánh đặc tính của bạn lên khi điều hướng.  
 * Tài liệu kiểm thử của bạn bao gồm các hướng dẫn trong các phần liên quan của file `README.MD` của bạn  
    _Tại sao_:  
    > Đo là ghi chú tiện dụng mà bạn để lại cho những nhà phát triển khác, các chuyên gia DevOps, QA hay bất kì ai có đủ 
    may mắn đề làm việc trên mã nguồn của bạn.  
## 6.Cấu trúc và đặt tên  
![Structure and Naming](https://github.com/wearehive/project-guidelines/raw/master/images/folder-tree.png)  
 * Tổ chức các file của bạn xung quanh các tính năng / các trang / các thành phần sản phẩm, không phải các vai trò. Mặt 
 khác, đặt các file kiểm thử của bạn bên cạnh các phần thực hiện của chúng.  
 
    **Bad**

    ```
    .
    ├── controllers
    |   ├── product.js
    |   └── user.js
    ├── models
    |   ├── product.js
    |   └── user.js
    ```

    **Good**

    ```
    .
    ├── product
    |   ├── index.js
    |   ├── product.js
    |   └── product.test.js
    ├── user
    |   ├── index.js
    |   ├── user.js
    |   └── user.test.js
    ```
    _Tại sao_:  
    > Thay cho danh sách dài các file, bạn sẽ tạo các module nhỏ bao gọn một nhiệm vụ, bao gồm cả kiểm thử của nó. Nó tạo 
    nhiều sự dễ dàng trong điều hướng và những thứ được tìm thấy trong thoáng chốc.  
 * Đặt các file test bổ sung vào các thư mục kiểm thử tiêng biệt để tránh sự nhầm lẫn  
    _Tại sao_:  
    > Nó là cách tiết kiệm thời gian cho những nhà phát triển khác hoặc các chuyên gia DevOps trong team của bạn  
 * Sử dụng thư mục `./config` và không tạo file cấu hình khác nhau cho môi trường khác nhau  
    _Tại sao_:  
    > Khi bạn phá vỡ file cấu hình cho những mục đích khác nhau (cơ sở dữ liệu, API, v.v..); đặt chúng trong thư mục với tên rất 
    dễ nhận biết như là `config` có ý nghĩa. Chỉ cần nhớ rằng không tạo các file cấu hình khác nhau cho các môi trường 
    khác nhau. Nó không tỷ lệ với độ sạch sẽ, vì khi tạo ra nhiều triển khai hơn của ứng dụng, tên môi trường mới là cần 
    thiết. Các giá trị được sử dụng trong file cấu hình cần được cung cấp bởi các biến môi trường. [đọc thêm](https://medium.com/@fedorHK/no-config-b3f1171eecd5)  
 * Đặt các bản thảo của bạn trong thư mục `./script`. Nó bao gồm các bản thảo `bash` và `node`.  
    _Tại sao_:  
    > Rất có thể bạn sẽ kết thúc với nhiều hơn một bản thảo, thiết kế sản xuất, thiết kế phát triển, bộ nạp cơ sở dữ liệu, 
    đồng bộ hóa cơ sở dữ liệu, v.v...  
 * Đặt các đầu ra thiết kế của bạn trong thư mục `./build`. thêm `build/` vào `.gitignore'.  
    _Tại sao_:  
    > Đặt tên cho nó với cái gì bạn thích, `dist` cũng dễ nghe. Nhưng hay chắc chắn giữ nó phù hợp với team của bạn. Những 
    gì bạn lấy được ở đây rất có thể là được tạo ra (đóng gói, biên dịch, chuyển đổi) hoặc di chuyển tới đó. Cái bạn tạo 
    ra là gì, bạn cùng team của bạn cũng có thể tạo ra, vì vậy không có điểm nào để bạn commit chúng lên kho điều hướng 
    của bạn. Trừ khi bạn đặc biệt muôn.  