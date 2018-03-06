<a name="testing"></a>
## 5. THỬ NGHIỆM
![Testing](/images/testing.png)
* Có một môi trường ở chế độ `test` nếu cần.

    _Tại sao:_
    > Đôi khi quá trình `end to end testing` trong chế độ `production`tương đối đầy đủ, đây là một số ngoại lệ: Một ví dụ bạn không muốn hiển thị chế độ 'production' và gây rối loạn hệ thống của người khác với dữ liệu thử nghiệm. 1 ví dụ khác là Api của bạn có thẻ có giới hạn về tỉ lệ trong chế độ `production` và chặn cuộc gọi thử nghiệm của bạn sau một số lượng yêu cầu nhất định.

* Đặt tệp kiểm tra của bạn bên cạnh các mô đun đã được thử nghiệm bằng cách sử dụng quy ước đặt tên `*.test.js` hoặc `*.spec.js`, như `moduleName.spec.js`.

    _Tại sao:_
    > Bạn không muốn tìm kiếm thông qua một cấu trúc thư mục để tìm một đơn vị test.[đọc thêm...](https://hackernoon.com/structure-your-javascript-code-for-testability-9bc93d9c72dc)
    

* Đặt các tệp thử nghiệm bổ sung của bạn vào một thư mục thử nghiệm riêng biệt để tránh nhầm lẫn.

    _Tại sao:_
    > Một số tập tin thử nghiệm không đặc biệt liên quan đến bất kỳ tập tin thực hiện cụ thể nào.Bạn phải đặt nó trong một thư mục có nhiều khả năng được tìm thấy bởi các nhà phát triển khác: thư mục `__test__`. Tên này : `__test__`  cũng là chuẩn hiện tại và được chọn bởi hầu hết các khuôn khổ thử nghiệm JavaScript.

* Viết mã kiểm chứng, tránh các tác dụng phụ **side effects**, giải nén các tác dụng phụ, viết các hàm thuần túy

    _Tại sao:_
    > Nếu bạn muốn thử nghiệm một business logic như một đơn vị riêng biệt. Bạn có thể "giảm thiểu tác động ngẫu nhiên và các quy trình không xác định đối với độ tin cậy trong code của bạn". [read more...](https://medium.com/javascript-scene/tdd-the-rite-way-53c9b46f45e3)
    
    > Một hàm thuần túy là một hàm luôn trả về cùng một đầu ra cho cùng một đầu vào. Ngược lại, một impure function là một chức năng có thể có các tác dụng phụ hoặc phụ thuộc vào các điều kiện từ bên ngoài để tạo ra một giá trị. Điều đó làm cho nó không dự đoán được. [read more...](https://hackernoon.com/structure-your-javascript-code-for-testability-9bc93d9c72dc)

* Sử dụng bộ kiểm tra tĩnh

    _Tại sao:_
    > Thỉnh thoảng chúng ta nên sử dụng bộ kiểm tra tĩnh. Nó mang lại sự tin cậy đối với sự chắc chắn trong code của bạn. [read more...](https://medium.freecodecamp.org/why-use-static-types-in-javascript-part-1-8382da1e0adb)


* Chạy test cục bộ trước khi lấy request từ `develop`.

    _Tại sao:_
    > Bạn không muốn là người xây dựng nhánh production-ready thất bạ. Chạy tests của bạn sau khi `rebase` và trước khi bạn đẩy nhánh tính năng mới lên trên một remote repository.

*   Tài liệu  của bạn bao gồm các hướng dẫn trong phần có liên quan của tập tin `README.md`.

    _Tại :_
    > Đây là một lưu ý tiện dụng bạn bỏ lại đằng sau cho các nhà phát triển khác hoặc chuyên gia DevOps hoặc QA hoặc bất cứ ai được may mắ để làm việc trên mã của bạn.n

<a name="structure-and-naming"></a>
## 6. Cấu trức và 
![Structure and Naming](/images/folder-tree.png)
* Tổ chức các tệp của bạn xung quanh các tính năng / trang / thành phần của sản phẩm chứ không phải các . Ngoài ra, đặt các tệp kiểm tra của bạn bên cạnh việc triển khai.


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

    _Tại s:_
    > Thay vì một danh sách dài các tệp tin, bạn sẽ tạo các mô-đun nhỏ gói gọn một trách nhiệm bao gồm kiểm tra và vân vân. Nó dễ dàng điều hướng hơn và mọi thứ có thể được tìm thấy trong nháy mắt.

* Đặt các tệp thử nghiệm bổ sung của bạn vào một thư mục thử nghiệm riêng biệt để tránh nhầm lẫn.

    _Tại sao:_
    > Đó là tiết kiệm thời gian cho các chuyên gia phát triển khác hoặc chuyên gia DevOps trong nhóm của bạn..

* Sử dụng 1 thư  `./config` và đừng khởi tạo files cấu hình khác nhau cho những môi trường khác nhau.

    _Tại sao:_
    >Khi bạn chia nhỏ tệp cấu hình cho các mục đích khác nhau (cơ sở dữ liệu, API và vân vân); đặt chúng vào một thư mục với một cái tên rất dễ nhận biết như config có ý nghĩa. Chỉ cần nhớ không phải để làm cho các tập tin cấu hình khác nhau cho các môi trường khác nhau. Nó không quy mô rõ ràng, khi ứng dụng nhiều ứng dụng được tạo ra, tên môi trường mới là cần thiết. Các giá trị được sử dụng trong tệp tin cấu hình nên được cung cấp bởi các biến môi trường [read more...](https://medium.com/@fedorHK/no-config-b3f1171eecd5)
    

* Đẩy scripts của bạn vào thư  `./scripts`. Scripts bao gồm `bash` và `node`.

    _Tại sao:_
    >Rất có thể tiến trình đó kết thúc với nhiều hơn một script, production build, development build, database feeders, database synchronization và vân .
    
* Đặt đầu ra bản build của bạn vào thư mục `./build`.Thêm `build/`  `.gitignore`.

    _Why:_
    >Đặt tên cho những gì bạn thích, `dist` cũng cool. Nhưng hãy đảm bảo giữ nó phù hợp với team của bạn. Những gì nhận được ở đó rất có thể được tạo ra (đóng gói, biên dịch, chuyển khoản) hoặc chuyển đến đó.Những gì bạn có thể tạo ra, đồng đội của bạn cũng có thể tạo ra, do đó, không có điểm cam kết chúng vào remote repository của bạn. Trừ khi bạn đặc biệt muốn.

<a name="code-style"></a>
## 7. Phong cách Code

![Code style](/images/code-style.png)

<a name="code-style-check"></a>
### 7.1 Some code style guidelines

* Sử dụng cú pháp JavaScript giai đoạn 2 và cao hơn (hiện đại) cho các dự án mới. Đối với dự án phù hợp với cú pháp hiện tại trừ khi bạn có ý định hiện đại hóa dự án.
    
    _Tại sao:_
    > Tất cả tùy thuộc vào bạn. Chúng tôi sử dụng transpilers để tận dụng các lợi thế cảu cú pháp. Giai đoạn 2 có nhiều khả năng trở thành 1 phần của spec với duy nhất những sửa đổi nhỏ. 

* Bao gồm kiểm tra kiểu mã trong quy trình xây dựng của bạn.

    _Tại sao:_
    > Phá bỏ kiểu build của bạn là một cách để thực thi phong cách code vào code của bạn. Nó ngăn cản việc bạn gọi nó một cách thiếu nghiêm túc. Làm nó cho cả client và server-side code. [read more...](https://www.robinwieruch.de/react-eslint-webpack-babel/)

* Sử dụng [ESLint - Pluggable JavaScript linter](http://eslint.org/) để thực thi phong cách code.

    _Tại sao:_
    > Chúng tôi đơn giản là thích `eslint`, Bạn thì không phải thích nó. Nó có nhiều quy tắc được hỗ trợ, khả năng cấu hình các quy tắc và khả năng thêm các quy tắc tùy chỉnh..

* Chúng tôi sử dụng [Airbnb JavaScript Style Guide](https://github.com/airbnb/javascript) đối với JavaScript, [Read more](https://www.gitbook.com/book/duk/airbnb-javascript-guidelines/details). Use the javascript style guide required by the project or your team.

* Chúng tôi sử dụng [Flow type style check rules for ESLint](https://github.com/gajus/eslint-plugin-flowtype) khi đang sử dụng [FlowType](https://flow.org/).

    _Why:_
    > Flow introduces few syntaxes that also need to follow certain code style and be checked.

* Sử dụng `.eslintignore` để loại bỏ files hoặc folders khi kiểm tra phong cách code.

    _Tại sao:_
    > Bạn không thể làm rối loạn code với `eslint-disable` bình luận bất cứ khi nào bạn cần loại trừ vài tập tin khi đang kiểm tra phong cách code.

* Xóa bất kỳ nhận xét nào bị tắt của bạn khỏi `eslint` trước khi thực hiện một Pull Request

    _Tại sao:_
    > Thật bình thường để kiểm tra tính năng không hoạt động trong khi làm việc trên một khối mã để tập trung nhiều hơn vào logic. Chỉ cần nhớ xóa những ý kiến `eslint-disable` này và thực hiện theo các quy tắc.

* Tùy thuộc vào kích thước của task sử dụng  `//TODO:` để comments hay mở tickets.

    _Tại sao:_
    > Do đó bạn có thể nhắc nhở bản thân và những người khác về một task nhỏ (như sắp xếp lại một chức năng hoặc cập nhật nhận xét. Đối với tasks lớn sử dụng `//TODO(#3456)` được thi hành bởi luật lint và số đó là một ticket mở.


* Luôn luôn comment và giữ chúng thích hợp như thay đổi code. Xóa những khối đã comment trong code.
    
    _Tại sao:_
    > Code của bạn nên là dễ đọc và khả thi, Bạn nên bỏ những gì làm mất tập trung. Nếu bạn sắp xếp lại function, không chỉ bình luận ra cái cũ , xóa nó đi.

* Tránh comment,logs hoặc đặt tên không liên quan hoặc hài hước.

    _Tại sao:_
    > Trong khi bạn xây dựng một tiến trình có thể(nên) loại bỏ chúng,Đôi khi nguồn code của bạn có thể được bàn giao cho công ty/khách hàng khác và họ sẽ không chia sẻ cùng với một người thích giễu cợt.

* Đặt tên của bạn có thể tìm kiếm với sự khác biệt có ý nghĩa tránh tên rút ngắn. Đối với các chức năng sử dụng dài, tên mô tả. Tên chức năng phải là một động từ hoặc động từ, và nó cần phải truyền đạt ý định của nó.

    _Tại sao:_
    > Nó giúp cho việc đọc mã nguồn tự nhiên hơn.

* Tổ chức các chức năng của bạn trong một tập tin theo nguyên tắc bước xuống. Chức năng cấp cao hơn nên ở trên và dưới ở dưới.

    _Tại sao:_
    > Nó giúp cho việc đọc mã nguồn tự nhiên hơn.

<a name="enforcing-code-style-standards"></a>
### 7.2 Thực thi các chuẩn phong cách code

* Sử dụng 1 file [.editorconfig](http://editorconfig.org/) giúp các nhà phát triển xác định và duy trì phong cách mã hóa nhất quán giữa các biên tập viên và IDE khác nhau trong dự án.
  
    _Tại sao:_
    > Dự án EditorConfig bao gồm định dạng tệp để định nghĩa kiểu mã hóa và một bộ sưu tập các plugin trình soạn thảo văn bản cho phép biên tập viên đọc định dạng tệp và tuân theo các kiểu được xác định. Các tập tin EditorConfig có thể đọc được dễ dàng và chúng hoạt động độc đáo với các hệ thống điều khiển phiên bản.
    
* Yêu cầu trình biên tập thông báo cho bạn về các lỗi về kiểu mã. Sử dụng [eslint-plugin-prettier](https://github.com/prettier/eslint-plugin-prettier) và [eslint-config-prettier](https://github.com/prettier/eslint-config-prettier) with your existing ESLint configuration. [read more...](https://github.com/prettier/eslint-config-prettier#installation)

* Xem xét sử dụng Git hooks.

    _Tại sao:_
    >Git hooks làm tăng đáng kể năng suất của một nhà phát triển. Thực hiện thay đổi, cam kết và đẩy vào môi trường dàn dựng hoặc sản xuất mà không sợ phá vỡ xây dựng [read more...](http://githooks.com/)

* Sử dụng Prettier với một precommit hook.

    _Tại sao:_
    > Mặc dù chính bản thân `prettier` có thể rất mạnh, nhưng nó không hiệu quả để chạy nó đơn giản như một nhiệm vụ NPM một mình để định dạng mã. Đây là nơi mà `lint-staged` (và `husky`) đi vào để hoạt động. đọc thêm về cách cấu hình `lint-staged` [here](https://github.com/okonet/lint-staged#configuration) and on configuring `husky` [here](https://github.com/typicode/husky).
 

<a name="logging"></a>
## 8. Logging

![Logging](/images/logging.png)

* tránh client-side điều khiển các bản ghi trong production

    _Tại sao:_
    > Mặc dù quá trình xây dựng của bạn có thể (nên) loại bỏ chúng, hãy chắc chắn rằng kiểm tra kiểu mã của bạn cảnh báo bạn về các bản ghi giao diện điều khiển còn sót lại.
    
* Tạo ra production logging có thể đọc được. Sử dụng các thư viện logging phù hợp  để sử dụng trong chế độ production (như là [winston](https://github.com/winstonjs/winston) hay
[node-bunyan](https://github.com/trentm/node-bunyan)).

    _Tại sao:_
    > Nó làm cho xử lý sự cố của bạn ít khó chịu với colorization, timestamps, đăng nhập vào một tập tin thêm vào giao diện điều khiển hoặc thậm chí đăng nhập vào một tập tin mà xoay hàng ngày. [read more...](https://blog.risingstack.com/node-js-logging-tutorial/)
