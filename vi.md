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
## 7. Phong cách code
 ![Code style](https://github.com/wearehive/project-guidelines/raw/master/images/code-style.png)    
 ### 7.1 Một vài hướng dẫn về phong cách code
 * Sử dụng stage-2 và cú pháp JavaScript cao hơn (hiện đại) cho dự án mới. Với những dự án cũ, duy trì sự tương thích với 
 những cú pháp đang tồn tại, trừ khi bạn có dự định cải tiến dự án.  
    _Tại sao_:  
    > Đó là tất cả vào bạn. Chúng tôi sử dụng những bộ chuyển đổi để sử dụng những tiện ích của bộ cú pháp mới. Stage-2 
    rất có thể sẽ trở thành một phần của spec chỉ với những thay đổi nhỏ.  
 * Tích hợp phong cách code của bạn vào tiến trình xây dựng  
    _Tại sao_:  
    > Phá vỡ thiết kế của bạn là một cách để thực hành phong cách code trong dự án của bạn. Thay đổi kiến trúc của bạn 
    là 1 trong những cách để áp dụng phong cách lập trình. Nó sẽ làm bản không cảm thấy nó bớt quan trọng đi. Áp dụng nó cho cả code bên phía client cũng như phía server. [đọc thêm](https://www.robinwieruch.de/react-eslint-webpack-babel/)  
    * Sử dụng [ESLint - Pluggable JavaScript linter](http://eslint.org/) để áp dụng phong cách lập trình.
    
      
    
        _Tại sao:_ 
    
        > Đơn giản là do chúng tôi thíchích `eslint` hơn, còn bạn thì không cần phải như vậy. Nó hỗ trợ nhiều luật hơn, có khả năng cấu hình lại các luật và khả năng thêm các luật tùy chỉnh nữa.
    
      
    
    * Chúng tôi sử dụng [hướng dẫn phong cách JavaScript Airbnb](https://github.com/airbnb/javascript) cho JavaScipt, [Đọc thêm](https://www.gitbook.com/book/duk/airbnb-javascript-guidelines/details).  Sử dụng hướng dẫn phong cách javascript phù hợp yêu cầu của dự án hoặc nhóm của bạn. 
    
      
    
    * Chúng tôi sử dụng [Phong cách kiểm tra luật dạng Flow cho ESLint](https://github.com/gajus/eslint-plugin-flowtype) khi sử dụng [FlowType](https://flow.org/). 
    
      
    
        _Tại sao:_ 
    
        > Flow cung cấp một vài cú pháp mà cần tuân theo phong cách lập trình cụ thể và cần được kiểm tra
    
      
    
    * Sử dụng `.eslintignore` để loại trù các file hay thư mục khỏi việc kiểm tra phong cách lập trình. 
    
      
    
        _Tại sao:_ 
    
    
        > Bạn không cần phải làm bẩn code của bạn với những dòng comment `eslint-disable` khi bạn cần loại các file ra khỏi việc kiểm tra phong cách.
    
      
    
    * Loại bỏ bất cứ comment tắt `eslint` của bạn trước khi tạo các Pull Request.
    
      
    
        _Tại sao:_ 
    
        > It's normal to disable style check while working on a code block to focus more on the logic. Just remember to remove those `eslint-disable` comments and follow the rules. 
        > Sẽ rất bình thường khi bạn tắt các kiểm tra phong cách trong khi làm việc trên 1 đoạn code để tập trung hơn vào logic. Hãy nhớ loại các comment `eslint-disable` và tuân theo các luật.
    
      
    
    * Phụ thuộc vào kích thước của công việc mà sử dụng các comment `//TODO:` hoặc mở thẻ.
    
      
    
        _Tại sao:_ 
    
        > Vì sau đó bạn có thể nhắc nhở bản thân hoặc người khác về các công việc nhỏ ( như là sắp xếp lại các hàm hoặc cập nhật các comment). Với các công việc lớn hơn sử dụng `//TODO(#3456)` được thực hiện bởi các luật và con số là 1 thẻ mở.
    
      
    
    * Luôn luôn comment liên quan những thay đổi của code. Loại bỏ các đoạn code được comment.
    
         
    
        _Tại sao:_ 
    
        > Code của bạn nênên càng dễ đọc càng tốt, bạn nên thoát ra khỏi những thứ gây xao nhãng. Nếu bạn sắp xếp lại các hàm, đừng chỉ comment những cái cũ, hãy xóa chúng đi. 
    
      
    
    * Tránh những comment, log hay cách đặt tên vui vẻ hay không liên quan.
    
      
    
        _Tại sao:_ 
    
        > Khi mà cái quy trình kiến trúc của bạn có thể(nên) tránh xa khỏi chúng, đôi khi mã nguồn của bạn có thể được bàn giao cho công ty/ khách hàng khác mà họ có thể không cười nhạo chúng.
    
      
    
    * Đặt tên  dễ tìm kiếm với nhưng ý nghĩa phân biệt tránh tên ngắn. Với các hàm sử dụng các tên dài, mang nghĩa mô tả. Tên của các hàm nên là 1 động từ hoặc cụm động từ, và nó cần liên quan đến chủ đích của hàm đó.
    
      
    
          _Tại sao:_ 
    
        > Nó làm cho việc đọc mã nguồn tự nhiên hơn.
    
      
    
    * Tổ chức các hàm của bạn trong 1 file dựa theo luật step-down. Những hàm ở mức cao hơn nên ở trên cùng và mức thấp thì ở bên dưới.
    
      
    
        _Tại sao:_ 
    
        > Nó làm cho việc đọc mã nguồn tự nhiên hơn.
    
      
    
    <a name="enforcing-code-style-standards"></a> 
    
    ### 7.2 Áp dụng các chuẩn phong cách lập trình 
    
      
    * Sử dụng 1 file [.editorconfig](http://editorconfig.org/) để giúp các lập trình viên định nghĩa và bảo trì phong cách lập trình thích hợp giữa các trình soạn thảo và các IDE khác nhau trên dự án
    
      
    
        _Tại sao:_ 
        > Dự án EditorConfig bao gồm các định dạng file để định nghĩa các phong cách lập trình và 1 tập các plugin của các trình soạn thảo văn bản cho phép các trình soạn thảo đọc các định dạng file và tuân theo để định nghĩa các phong cách, Các file EditorConfig cũng rất dễ đọc và nó cũng tương tác hiệu quả với các hệ thống quản lý phiên bản.
    
      
    
    * Để các trình soạn thảo thông báo cho bạn về các lỗi phong  cách lập trình. Sử dụng [eslint-plugin-prettier](https://github.com/prettier/eslint-plugin-prettier) và [eslint-config-prettier](https://github.com/prettier/eslint-config-prettier) với các cấu hình ESLint hiện tại của bạn. [đọc thêm...](https://github.com/prettier/eslint-config-prettier#installation) 
    
      
    
    * Xem xét sử dụng Git hooks.
    
      
    
        _Tại sao:_ 
    
    
        > Git hooks sẽ tăng mạnh năng suất của các lập trình viên. Chúng ta có thể tạo các thay đổi, commit và push lên môi trường staging hoặc production mà không sợ phá vỡ kiến trúc. [đọc thêm...](http://githooks.com/) 
    
      
    
    * Sử dụng Prettier với precommit hook
    
      
    
        _Tại sao:_ 
    
        > Vì bản thân `prettier` nó rất mạnh, nên việc đơn giản chạy nó như nhưng công việc npm độc lập mỗi lần để chỉnh sửa code sẽ không năng suất lắm. Đây cũng là lúc mà `lint-staged` ( và `husky`) trở nên quan trọng. Đọc thêm về cấu hình `lint-staged` [ở đây](https://github.com/okonet/lint-staged#configuration)
     và cấu hình `husky` [ở đây](https://github.com/typicode/husky).
      
## 8. Ghi log  
![logging](https://github.com/thanhbinhhd/project-guidelines/raw/master/images/logging.png)  
 * Tránh hiển thị màn hình log phía bên người dùng trong sản xuất  
    _Tại sao_:  
    > Mặc dù tiến trình xây dựng của bạn có thể thoát khỏi chúng, hãy chắc chắn rằng bộ kiểm thử phong cách code của bạn 
    cảnh báo bạn về những bảng console log còn ở lại.  
 * Sản phẩm cũng có thể đọc được production logging. Sử dụng thư viện logging để dùng trong chế độ sản xuất (chẳng hạn như 
 [winston](https://github.com/winstonjs/winston) hoặc [node-bunyan](https://github.com/trentm/node-bunyan))  
    _Tại sao_:  
    > Nó làm cho quá trinh gỡ rối của bạn đỡ khó chịu hơn với  colorization, timestamps, log đến mội file trong cửa sổ mở 
    rộng hoặc bất kì file logging nào xoay hàng ngày. [đọc thêm](https://blog.risingstack.com/node-js-logging-tutorial/)  