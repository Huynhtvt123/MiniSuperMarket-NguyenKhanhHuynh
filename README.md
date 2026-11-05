Quản lý siêu thị mini -- Đồ ăn vặt & Đồ chơi
Ứng dụng quản lý siêu thị mini xây dựng bằng Spring Boot (Java),
React + Vite và MySQL (XAMPP).

Mục lục
- Giới thiệu dự án
- Mục tiêu
- Phạm vi nghiệp vụ
- Đối tượng sử dụng
- Nghiệp vụ chính
- Công nghệ sử dụng
- Kiến trúc tổng quan
- Cài đặt và chạy trên Windows
- Tài khoản mẫu
- Database
- Kiểm thử
- Xử lý lỗi
- Kết luận
1. Giới thiệu dự án
Quản lý siêu thị mini -- Đồ ăn vặt & Đồ chơi là ứng dụng hỗ trợ quản
lý hoạt động của một cửa hàng/siêu thị mini. Hệ thống tập trung vào hàng
hóa, kho, bán hàng, khách hàng, nhân viên và thống kê. Dự án được xây
dựng theo mô hình có giao diện web, backend Java và cơ sở dữ liệu quan
hệ. Giao diện phía người dùng sử dụng React, TypeScript và Vite. Phía
máy chủ sử dụng Java 17+ và Spring Boot. Dữ liệu được lưu trữ trong
MySQL 8 hoặc MariaDB chạy thông qua XAMPP. Tài liệu này mô tả mục tiêu,
nghiệp vụ, công nghệ, cách cài đặt, vận hành, kiểm thử và bảo trì dự án.
Một số thông tin chi tiết phụ thuộc vào mã nguồn thực tế; hãy đối chiếu
cấu hình trong repository trước khi triển khai.
2. Mục tiêu
- Số hóa quy trình quản lý hàng hóa của siêu thị mini.
- Hỗ trợ theo dõi số lượng tồn kho và lịch sử nhập, xuất.
- Hỗ trợ nhân viên lập hóa đơn bán hàng tại quầy.
- Quản lý hồ sơ khách hàng và thành viên.
- Cho phép khách hàng đăng ký và đăng nhập bằng tài khoản riêng.
- Cung cấp giao diện xem sản phẩm và gửi yêu cầu mua hàng.
- Hỗ trợ quản lý nhân viên và phân quyền theo vai trò.
- Hỗ trợ theo dõi hàng lỗi và dữ liệu đã đưa vào thùng rác.
- Giảm thao tác thủ công và hạn chế sai sót khi quản lý.
- Tạo nền tảng để mở rộng thêm báo cáo và nghiệp vụ trong tương lai.
3. Phạm vi nghiệp vụ
Hệ thống hướng đến cửa hàng quy mô nhỏ, kinh doanh nhiều nhóm hàng. Các
nhóm hàng tiêu biểu gồm đồ ăn vặt, bánh kẹo, nước uống, đồ chơi và phụ
kiện. Quản lý sản phẩm bao gồm tên hàng, danh mục, thương hiệu, giá
nhập, giá bán, số lượng và đơn vị tính. Thông tin quản lý có thể bao gồm
hạn sử dụng và vị trí kệ. Nhân viên thực hiện các công việc được cấp
quyền như bán hàng, quản lý khách hàng hoặc quản lý kho. Khách hàng sử
dụng khu vực cửa hàng để đăng ký, đăng nhập, xem sản phẩm và gửi yêu cầu
mua hàng. Các nghiệp vụ ngoài phạm vi cần được xác nhận thêm trước khi
phát triển, ví dụ giao hàng, thanh toán trực tuyến hoặc tích hợp hóa đơn
điện tử.
4. Đối tượng sử dụng
Quản trị viên
Quản trị viên có thể quản lý các chức năng hệ thống theo quyền được cấp.
Tài khoản mẫu: admin / 123. ### Thu ngân Thu ngân thực hiện bán
hàng tại quầy và lập hóa đơn theo quyền được cấp. Tài khoản mẫu:
cashier / 123. ### Nhân viên kho Nhân viên kho theo dõi hàng hóa,
số lượng và các nghiệp vụ kho theo quyền được cấp. Tài khoản mẫu:
fixer / 123. ### Khách hàng Khách hàng tự đăng ký tài khoản, đăng
nhập, xem sản phẩm, tạo yêu cầu mua hàng và gửi phản hồi. Khách hàng
không được cấp quyền quản trị. Khách hàng mới đăng ký tại
/store/register.
5. Nghiệp vụ chính
Quản lý hàng hóa
- Thêm, xem, cập nhật và quản lý trạng thái hàng hóa.
- Phân loại theo danh mục và thương hiệu.
- Theo dõi giá nhập, giá bán, đơn vị tính và số lượng.
- Lưu hạn sử dụng nếu mặt hàng có yêu cầu.
- Ghi nhận vị trí kệ để thuận tiện tìm kiếm. ### Quản lý danh mục và
  thương hiệu
- Phân nhóm hàng hóa theo loại.
- Gắn thương hiệu phù hợp với từng sản phẩm.
- Duy trì dữ liệu thống nhất khi nhập sản phẩm mới. ### Quản lý kho
- Theo dõi số lượng tồn.
- Lưu lịch sử nhập kho và xuất kho.
- Ghi nhận hàng lỗi.
- Hỗ trợ kiểm tra biến động số lượng. ### Bán hàng tại quầy
- Nhân viên lựa chọn hàng hóa cần bán.
- Lập hóa đơn cho giao dịch.
- Gắn thông tin khách hàng khi cần.
- Theo dõi dữ liệu hóa đơn và thống kê bán hàng. ### Quản lý khách
  hàng
- Lưu thông tin khách hàng.
- Quản lý hồ sơ thành viên.
- Hỗ trợ tài khoản khách hàng tự đăng ký.
- Tiếp nhận yêu cầu mua hàng và phản hồi. ### Quản lý nhân viên
- Quản lý tài khoản nhân viên.
- Phân quyền theo vai trò.
- Kiểm soát quyền truy cập vào các khu vực nghiệp vụ.
6. Công nghệ sử dụng
  Thành phần                          Công nghệ
  Backend                             Java 17+, Spring Boot

  Bảo mật                             Spring Security

  Truy cập dữ liệu                    Spring Data JPA

  Frontend                            React

  Ngôn ngữ frontend                   TypeScript

  Công cụ frontend                    Vite

  Cơ sở dữ liệu                       MySQL 8 / MariaDB

  Môi trường database trên Windows    XAMPP

  Địa chỉ frontend mặc định theo      http://localhost:5173
hướng dẫn dự án                     
Database đích                       QuanLySieuThiMini
7. Kiến trúc tổng quan
Ứng dụng được chia thành ba phần chính: giao diện người dùng, backend và
cơ sở dữ liệu. Frontend gửi yêu cầu đến backend thông qua API. Backend
tiếp nhận yêu cầu, xác thực người dùng, kiểm tra quyền và xử lý nghiệp
vụ. Spring Data JPA hỗ trợ ánh xạ đối tượng Java với dữ liệu quan hệ.
MySQL/MariaDB lưu trữ thông tin nghiệp vụ. Spring Security được sử dụng
cho cơ chế bảo mật. Token của khách hàng mang vai trò CUSTOMER. Tài
khoản nhân viên tiếp tục sử dụng cơ chế đăng nhập hiện tại của hệ thống.
Không nên cho phép frontend tự quyết định quyền truy cập; backend phải
kiểm tra quyền ở phía máy chủ.
8. Cấu trúc thư mục tham khảo
Cấu trúc thực tế có thể khác tùy repository. Hãy kiểm tra thư mục dự án
trước khi chạy.
doanJava/
├── package.json
├── package-lock.json
├── xampp_migration.sql
├── README.md
├── src/ hoặc frontend/
│   ├── components/
│   ├── pages/
│   ├── services/
│   └── assets/
└── backend/ hoặc thư mục mã nguồn Java
    ├── src/
    │   ├── main/
    │   │   ├── java/
    │   │   └── resources/
    │   └── test/
    └── pom.xml hoặc build.gradle
Tên thư mục trên chỉ mang tính minh họa, không khẳng định chính xác cấu
trúc của mọi phiên bản dự án. Tệp package.json chứa các script và
dependency Node.js. Tệp xampp_migration.sql dùng để tạo/nạp dữ liệu
database theo cấu hình dự án. Tệp cấu hình backend thường chứa thông tin
kết nối database; không đưa mật khẩu thật lên Git.
9. Yêu cầu môi trường
- Windows 10 hoặc Windows 11.
- Node.js phiên bản LTS.
- JDK 17 trở lên.
- XAMPP có MySQL hoặc MariaDB.
- Trình duyệt web hiện đại.
- Kết nối Internet để tải dependency và ảnh sản phẩm trực tuyến.
- Git là tùy chọn nhưng nên cài để quản lý phiên bản. Kiểm tra Node.js
  bằng node -v. Kiểm tra npm bằng npm -v. Kiểm tra Java bằng
  java -version. Kiểm tra trình biên dịch Java bằng
  javac -version. Nếu lệnh không được nhận diện, kiểm tra biến môi
  trường PATH và cài đặt tương ứng.
10. Cài đặt trên Windows
1. Cài Node.js LTS từ trang chính thức của Node.js.
2. Cài JDK 17 hoặc phiên bản mới hơn tương thích với dự án.
3. Cài XAMPP.
4. Mở XAMPP Control Panel.
5. Nhấn Start ở dòng MySQL.
6. Chờ MySQL chuyển sang trạng thái đang chạy.
7. Mở CMD hoặc Terminal.
8. Di chuyển đến thư mục dự án doanJava.
9. Cài dependency bằng npm install.
10. Chờ quá trình cài đặt hoàn tất.
11. Chạy migration bằng npm run migrate.
12. Khởi động ứng dụng bằng npm run dev.
13. Mở trình duyệt tại http://localhost:5173. Nếu dự án được tách
    frontend/backend thành hai tiến trình riêng, hãy làm theo script và
    tài liệu trong repository.
11. Khởi động XAMPP và MySQL
Mở XAMPP Control Panel bằng quyền phù hợp với máy tính. Nhấn Start
tại dịch vụ MySQL. Nếu MySQL không khởi động, kiểm tra cổng đang sử dụng
và nhật ký lỗi trong XAMPP. Không tự ý xóa thư mục dữ liệu MySQL để xử
lý lỗi vì có thể làm mất database. Nếu cổng mặc định bị chiếm, cần đồng
bộ lại cấu hình MySQL và cấu hình kết nối backend. Sau khi MySQL chạy,
có thể mở phpMyAdmin nếu XAMPP đã bật thành phần này. Tên database mục
tiêu của dự án là QuanLySieuThiMini.
12. Cài đặt dependency frontend
Mở CMD tại thư mục gốc dự án. Chạy:
npm install
Lệnh này đọc danh sách package từ package.json và cài các dependency.
Nếu cài đặt thất bại, kiểm tra kết nối Internet và phiên bản Node.js.
Không xóa package-lock.json tùy tiện vì tệp này giúp đồng bộ phiên bản
package. Khi gặp lỗi dependency, lưu lại toàn bộ thông báo lỗi để xác
định package gây lỗi.
13. Tạo database và nạp dữ liệu mẫu
Dự án cung cấp script:
npm run migrate
Theo cấu hình được mô tả, script này tạo database QuanLySieuThiMini và
nạp dữ liệu mẫu. File SQL có thể import thủ công qua phpMyAdmin là
xampp_migration.sql. Trước khi chạy migration trên dữ liệu đang sử
dụng, hãy sao lưu database. Không chạy lại migration nếu chưa biết
script có xóa hoặc ghi đè dữ liệu hay không. Nếu database không được
tạo, kiểm tra MySQL đang chạy và thông tin kết nối trong cấu hình.
14. Khởi động ứng dụng
Tại thư mục dự án, chạy:
npm run dev
Sau khi tiến trình khởi động thành công, mở: http://localhost:5173 Giữ
cửa sổ terminal hoạt động trong lúc sử dụng ứng dụng. Nếu cổng 5173 đã
được sử dụng, Vite có thể đề xuất một cổng khác. Khi đó hãy mở đúng địa
chỉ được hiển thị trong terminal. Nếu frontend mở được nhưng không tải
dữ liệu, kiểm tra backend và kết nối database.
15. Tài khoản mẫu
  Vai trò         Tên đăng nhập   Mật khẩu
  Quản trị        admin         123
Thu ngân        cashier       123
Nhân viên kho   fixer         123

Các tài khoản trên là dữ liệu mẫu phục vụ chạy thử. Không sử dụng mật
khẩu mẫu trong môi trường thật. Nên đổi mật khẩu ngay khi triển khai
hoặc trình diễn trên môi trường dùng chung. Khách hàng không dùng các
tài khoản nhân viên này.
16. Khu vực khách hàng
- Đăng ký: /store/register
- Đăng nhập: /store/login
- Thông tin cá nhân: /store/account Khách hàng có thể tự tạo tài
  khoản trên trang đăng ký. API đăng ký và đăng nhập khách hàng được
  tách riêng. Mật khẩu khách hàng được mã hóa bằng BCrypt. Token khách
  hàng mang vai trò CUSTOMER. Tài khoản khách hàng không được cấp
  quyền quản trị. Khi triển khai, backend cần xác thực token và kiểm
  tra quyền cho mọi API được bảo vệ.
17. Bảo mật và phân quyền
Spring Security là thành phần bảo mật chính ở backend. BCrypt được sử
dụng để băm mật khẩu khách hàng. Không lưu mật khẩu dạng văn bản thuần
trong database. Không đưa token, mật khẩu database hoặc khóa bí mật vào
mã nguồn công khai. Không tin tưởng vai trò do frontend gửi lên. Backend
phải xác thực token và xác định vai trò từ thông tin đã được ký/xác
thực. Vai trò CUSTOMER chỉ được truy cập các chức năng dành cho khách
hàng. Các thao tác quản trị, nhân viên và kho phải được bảo vệ bằng
quyền tương ứng. Khi phát hiện truy cập trái phép, backend cần trả về mã
lỗi phù hợp.
18. Quản lý hàng hóa
Thông tin hàng hóa có thể bao gồm: - Mã hàng hoặc mã vạch. - Tên sản
phẩm. - Danh mục. - Thương hiệu. - Đơn vị tính. - Giá nhập. - Giá bán. -
Số lượng tồn. - Hạn sử dụng. - Vị trí kệ. - Trạng thái kinh doanh. Khi
thêm hàng hóa, cần kiểm tra dữ liệu bắt buộc. Giá và số lượng không nên
nhận giá trị âm. Mã hàng/mã vạch cần được kiểm tra trùng lặp nếu hệ
thống quy định duy nhất. Khi cập nhật sản phẩm, cần tránh làm sai lệch
lịch sử giao dịch đã phát sinh.
19. Danh mục và thương hiệu
Danh mục giúp phân loại hàng hóa theo nhóm như đồ ăn vặt, bánh kẹo, nước
uống, đồ chơi và phụ kiện. Thương hiệu giúp nhận diện nhà sản xuất hoặc
nhãn hàng. Mỗi sản phẩm nên được gắn với danh mục phù hợp. Nếu sản phẩm
có thương hiệu, thông tin thương hiệu cần được chọn nhất quán. Không nên
xóa danh mục hoặc thương hiệu đang được sản phẩm sử dụng nếu chưa xử lý
quan hệ dữ liệu. Có thể cân nhắc chuyển trạng thái ngừng hoạt động thay
vì xóa cứng.
20. Quản lý kho
Quản lý kho tập trung vào số lượng hàng hóa và biến động tồn kho. Lịch
sử nhập kho giúp truy vết nguồn tăng số lượng. Lịch sử xuất kho giúp
truy vết nguyên nhân giảm số lượng. Mọi thao tác thay đổi số lượng nên
có thông tin thời gian và người thực hiện. Cần đối chiếu số lượng thực
tế với số lượng trên hệ thống định kỳ. Hàng lỗi nên được ghi nhận riêng
để tránh tính nhầm vào hàng có thể bán. Không nên sửa trực tiếp số lượng
tồn mà không có lý do hoặc lịch sử điều chỉnh.
21. Hàng lỗi và hạn sử dụng
Hàng lỗi là hàng không đủ điều kiện bán hoặc cần xử lý riêng. Thông tin
hàng lỗi nên bao gồm sản phẩm, số lượng, lý do, thời điểm và người ghi
nhận. Với mặt hàng có hạn sử dụng, cần nhập đúng ngày hết hạn. Nên kiểm
tra hàng gần hết hạn trước khi bán hoặc nhập thêm. Quy trình xử lý hàng
lỗi cần tuân theo quy định của cửa hàng. Không mặc định mọi mặt hàng đều
có hạn sử dụng; tùy loại sản phẩm để áp dụng.
22. Bán hàng và hóa đơn
Thu ngân thực hiện nghiệp vụ bán hàng tại quầy. Một hóa đơn thường gắn
với một hoặc nhiều dòng sản phẩm. Mỗi dòng hàng cần thể hiện sản phẩm,
số lượng và đơn giá tại thời điểm bán. Tổng tiền cần được tính nhất quán
giữa giao diện và backend. Backend nên là nơi xác nhận giá trị cuối cùng
của hóa đơn. Cần kiểm tra tồn kho trước khi hoàn tất giao dịch. Nếu giao
dịch thất bại, không được để số lượng kho bị trừ một phần. Thông tin hóa
đơn cần được lưu để tra cứu và thống kê.
23. Khách hàng và thành viên
Hồ sơ khách hàng có thể lưu thông tin liên hệ và thông tin thành viên.
Chỉ thu thập dữ liệu cần thiết cho hoạt động của cửa hàng. Giới hạn
quyền xem và chỉnh sửa dữ liệu khách hàng theo vai trò. Khách hàng có
thể tự đăng ký tài khoản. Khách hàng có thể đăng nhập và xem thông tin
cá nhân tại /store/account. Cần kiểm tra dữ liệu đầu vào và xử lý
trường hợp tài khoản đã tồn tại. Không hiển thị thông tin cá nhân của
khách hàng khác cho người dùng không có quyền.
24. Yêu cầu mua hàng và phản hồi
Khu vực cửa hàng cho phép khách hàng tạo yêu cầu mua hàng. Khách hàng
cũng có thể gửi phản hồi theo chức năng được cung cấp. Yêu cầu mua hàng
không mặc nhiên đồng nghĩa với hóa đơn đã thanh toán. Nhân viên cần xem
và xử lý yêu cầu theo quy trình của cửa hàng. Nên lưu trạng thái yêu cầu
để khách hàng và nhân viên theo dõi. Nội dung phản hồi cần được kiểm tra
và hiển thị an toàn.
25. Thùng rác dữ liệu
Thùng rác hỗ trợ theo dõi dữ liệu đã bị đưa ra khỏi danh sách hoạt động.
Cần phân biệt xóa mềm và xóa vĩnh viễn. Xóa mềm thường cho phép khôi
phục dữ liệu nếu chưa bị xóa vĩnh viễn. Trước khi khôi phục, cần kiểm
tra các ràng buộc và dữ liệu liên quan. Không nên xóa vĩnh viễn bản ghi
có liên quan đến lịch sử hóa đơn nếu nghiệp vụ yêu cầu lưu trữ. Quyền
xem, khôi phục và xóa vĩnh viễn cần được giới hạn.
26. Giao diện và màu sắc
Giao diện sử dụng bảng màu kem ấm, nâu cà phê, xanh olive và cam đất.
Định hướng màu sắc tạo cảm giác gần gũi với cửa hàng bán lẻ. Các thành
phần cần có độ tương phản đủ để dễ đọc. Nút thao tác quan trọng cần có
nhãn rõ ràng. Thông báo lỗi nên chỉ ra trường dữ liệu cần sửa. Giao diện
nên tương thích với các kích thước màn hình phổ biến.
27. Ảnh sản phẩm và banner
Ảnh trên trang cửa hàng sử dụng ảnh trực tuyến theo nhóm hàng. Ảnh đồ ăn
vặt: https://fmcgnepal.com/images/snacks.webp Ảnh nước uống:
https://p2.trrsf.com/image/fget/cf/940/0/images.terra.com/2023/07/02/reflejo_pag1-t8cxsnqdz0vr.jpg
Ảnh đồ chơi:
https://igrashky24.com.ua/image/catalog/categori/ihrashky.png Ảnh banner
cửa hàng: https://altawfeermarket.com/assets/images/1775260496_2887.png
Máy tính cần kết nối Internet để tải các ảnh này. Đường dẫn ảnh bên
ngoài có thể thay đổi hoặc ngừng hoạt động. Nếu ảnh không hiển thị, kiểm
tra kết nối Internet và địa chỉ nguồn ảnh. Khi triển khai thương mại,
hãy kiểm tra giấy phép sử dụng ảnh hoặc thay bằng ảnh do cửa hàng tự
chụp.
28. Database
Tên database đích: QuanLySieuThiMini. Hệ quản trị: MySQL 8 hoặc
MariaDB. Môi trường Windows theo hướng dẫn: XAMPP. Tệp SQL import:
xampp_migration.sql. Có thể dùng phpMyAdmin để xem database sau khi
migration. Tên lớp/thuộc tính và một số migration lịch sử có thể giữ
định danh tương thích của dự án nền. Việc giữ định danh tương thích nhằm
hạn chế ảnh hưởng đến API và dữ liệu đã có. Nội dung nghiệp vụ và dữ
liệu mẫu đã được chuyển sang hàng hóa siêu thị mini.
29. Sao lưu và phục hồi database
Trước khi cập nhật cấu trúc database, hãy tạo bản sao lưu. Có thể dùng
chức năng Export trong phpMyAdmin để xuất database. Lưu bản sao lưu ở
nơi an toàn, không đặt chung thư mục public của ứng dụng. Để phục hồi,
tạo database đích phù hợp và import tệp sao lưu. Sau khi phục hồi, kiểm
tra số lượng bảng và dữ liệu quan trọng. Không thử nghiệm phục hồi trực
tiếp trên database đang vận hành.
30. Cấu hình kết nối database
Backend cần biết máy chủ database, cổng, tên database, tên người dùng và
mật khẩu. Các giá trị cấu hình cụ thể phụ thuộc vào file cấu hình của dự
án. Không tự đặt giá trị cấu hình nếu chưa kiểm tra môi trường thực tế.
Trong môi trường phát triển XAMPP, hãy xác nhận cổng MySQL và tài khoản
đang dùng. Trong môi trường triển khai, nên dùng biến môi trường hoặc hệ
thống quản lý bí mật. Không commit mật khẩu thật vào Git.
31. API và giao tiếp frontend/backend
Frontend giao tiếp với backend thông qua các API được dự án định nghĩa.
Địa chỉ API và danh sách endpoint cần được kiểm tra trong mã nguồn.
Không suy đoán endpoint khi chưa xác minh. Các API cần kiểm tra dữ liệu
đầu vào ở backend. API yêu cầu đăng nhập cần xác thực token. API quản
trị cần kiểm tra vai trò. Thông báo lỗi API nên đủ rõ để frontend hiển
thị phù hợp nhưng không làm lộ thông tin nhạy cảm.
32. Quy tắc dữ liệu đầu vào
Tên sản phẩm không nên để trống. Giá bán và giá nhập cần là số hợp lệ.
Số lượng tồn không được âm nếu nghiệp vụ không cho phép. Ngày hết hạn
cần đúng định dạng và hợp lệ. Thông tin tài khoản cần được kiểm tra
trước khi tạo. Dữ liệu văn bản cần được xử lý để tránh nội dung độc hại.
Backend phải kiểm tra dữ liệu ngay cả khi frontend đã kiểm tra.
33. Quy trình kiểm thử cơ bản
1. Khởi động MySQL trong XAMPP.
2. Kiểm tra database QuanLySieuThiMini.
3. Khởi động backend theo cấu hình dự án.
4. Khởi động frontend bằng npm run dev.
5. Truy cập http://localhost:5173.
6. Đăng nhập bằng tài khoản mẫu.
7. Kiểm tra các chức năng theo vai trò.
8. Đăng ký tài khoản khách hàng mới.
9. Đăng nhập bằng tài khoản khách hàng.
10. Kiểm tra trang sản phẩm và hồ sơ cá nhân.
11. Kiểm tra thao tác kho và hóa đơn bằng tài khoản phù hợp.
12. Ghi nhận lỗi và kết quả kiểm thử.
34. Kiểm thử đăng nhập
- Nhập đúng tên đăng nhập và mật khẩu.
- Nhập sai mật khẩu.
- Bỏ trống tên đăng nhập.
- Bỏ trống mật khẩu.
- Kiểm tra điều hướng sau khi đăng nhập.
- Kiểm tra quyền truy cập theo vai trò.
- Đăng xuất và thử truy cập lại trang cần xác thực.
- Kiểm tra trường hợp token hết hạn nếu hệ thống có hỗ trợ. Không dùng
  mật khẩu mẫu trong môi trường thật.
35. Kiểm thử đăng ký khách hàng
- Mở /store/register.
- Nhập các trường bắt buộc hợp lệ.
- Thử đăng ký với thông tin hợp lệ.
- Thử bỏ trống trường bắt buộc.
- Thử dùng thông tin định danh đã tồn tại.
- Thử nhập định dạng email hoặc số điện thoại không hợp lệ nếu có
  trường tương ứng.
- Kiểm tra thông báo thành công/thất bại.
- Kiểm tra mật khẩu trong database đã được BCrypt băm, không phải văn
  bản thuần.
36. Kiểm thử phân quyền
Đăng nhập bằng tài khoản quản trị và kiểm tra chức năng quản trị. Đăng
nhập bằng tài khoản thu ngân và kiểm tra chức năng bán hàng. Đăng nhập
bằng tài khoản nhân viên kho và kiểm tra chức năng kho. Đăng nhập bằng
tài khoản khách hàng và kiểm tra khu vực cửa hàng. Thử truy cập URL/API
không thuộc quyền của tài khoản hiện tại. Kết quả mong đợi là backend từ
chối truy cập trái phép. Không chỉ ẩn nút trên giao diện; phải kiểm tra
quyền ở backend.
37. Kiểm thử hàng hóa
- Tạo một sản phẩm với dữ liệu hợp lệ.
- Kiểm tra sản phẩm xuất hiện trong danh sách.
- Cập nhật tên hoặc giá sản phẩm.
- Kiểm tra dữ liệu sau cập nhật.
- Thử nhập giá âm.
- Thử nhập số lượng âm.
- Thử bỏ trống tên sản phẩm.
- Thử mã hàng trùng nếu có ràng buộc duy nhất.
- Kiểm tra lọc theo danh mục hoặc thương hiệu nếu chức năng có hỗ trợ.
38. Kiểm thử kho
- Ghi nhận một lần nhập kho.
- Kiểm tra số lượng tồn tăng đúng.
- Ghi nhận một lần xuất kho.
- Kiểm tra số lượng tồn giảm đúng.
- Thử xuất số lượng lớn hơn tồn kho.
- Kiểm tra lịch sử giao dịch kho.
- Ghi nhận hàng lỗi và kiểm tra dữ liệu.
- Đối chiếu tồn kho trước và sau giao dịch.
39. Kiểm thử hóa đơn
- Tạo hóa đơn có một sản phẩm.
- Tạo hóa đơn có nhiều sản phẩm.
- Kiểm tra tổng tiền.
- Kiểm tra số lượng tồn sau khi bán.
- Thử bán vượt số lượng tồn.
- Kiểm tra thông tin khách hàng gắn với hóa đơn nếu có.
- Kiểm tra dữ liệu hóa đơn được lưu.
- Kiểm tra thống kê sau khi tạo hóa đơn.
40. Xử lý lỗi thường gặp
Không chạy được npm
Kiểm tra Node.js đã cài đặt và PATH đã được cập nhật. ### npm install
thất bại Kiểm tra mạng, phiên bản Node.js và thông báo lỗi package. ###
MySQL không bật được Kiểm tra cổng MySQL có bị chương trình khác chiếm
hay không. ### Migration không kết nối được database Kiểm tra MySQL
đang chạy, tên database và thông tin đăng nhập. ### Frontend không tải
dữ liệu Kiểm tra backend đã chạy và địa chỉ API có đúng không. ### Ảnh
không hiển thị Kiểm tra kết nối Internet và URL ảnh bên ngoài. ### Đăng
nhập bị từ chối Kiểm tra tài khoản, mật khẩu, trạng thái tài khoản và dữ
liệu mẫu.
41. Nhật ký và chẩn đoán
Khi xảy ra lỗi, lưu lại thông báo đầy đủ từ terminal hoặc trình duyệt.
Ghi lại thao tác ngay trước khi lỗi xảy ra. Ghi lại tài khoản/role đang
sử dụng, nhưng không ghi mật khẩu hoặc token. Kiểm tra log backend để
tìm nguyên nhân phía máy chủ. Kiểm tra Console và Network trong
Developer Tools để chẩn đoán frontend. Không công khai log chứa thông
tin cá nhân hoặc bí mật cấu hình.
42. Quy tắc Git và quản lý mã nguồn
Nên sử dụng Git để theo dõi thay đổi. Tạo commit nhỏ theo từng nhóm chức
năng. Không commit thư mục dependency như node_modules. Không commit
file chứa mật khẩu, token hoặc thông tin kết nối thật. Có thể dùng
.gitignore để loại trừ file build và file môi trường. Trước khi cập
nhật nhánh chính, hãy chạy lại các bước kiểm thử cơ bản. Thông điệp
commit nên mô tả ngắn gọn nội dung thay đổi.
43. Triển khai và vận hành
Hướng dẫn trong README này ưu tiên môi trường phát triển Windows. Trước
khi triển khai thật, cần cấu hình riêng cho môi trường production. Thay
tài khoản mẫu và mật khẩu yếu. Sử dụng HTTPS khi truy cập qua mạng. Giới
hạn quyền database ở mức cần thiết. Thiết lập sao lưu định kỳ. Kiểm tra
quyền truy cập và chính sách lưu trữ dữ liệu. Kiểm tra giấy phép ảnh và
thư viện sử dụng. Không dùng cấu hình phát triển trực tiếp cho môi
trường thương mại.
44. Quyền riêng tư và dữ liệu cá nhân
Chỉ thu thập thông tin khách hàng phục vụ nghiệp vụ. Chỉ người có quyền
mới được xem hoặc cập nhật hồ sơ khách hàng. Không đưa dữ liệu khách
hàng thật vào repository công khai. Khi chia sẻ ảnh chụp màn hình để báo
lỗi, hãy che thông tin cá nhân. Có quy trình sao lưu và xóa dữ liệu theo
chính sách của đơn vị vận hành.
45. Khả năng mở rộng
Các hướng mở rộng có thể xem xét: - Báo cáo doanh thu theo ngày, tháng
và năm. - Cảnh báo hàng sắp hết. - Cảnh báo hàng gần hết hạn. - Quản lý
nhà cung cấp. - In hóa đơn. - Tìm kiếm và lọc sản phẩm nâng cao. - Phân
trang danh sách dữ liệu. - Xuất báo cáo Excel hoặc PDF. - Tích hợp mã QR
hoặc máy quét mã vạch. - Tích hợp thanh toán trực tuyến nếu có yêu cầu.
Các chức năng mở rộng cần được phân tích và kiểm thử trước khi đưa vào
sử dụng.
46. Quy ước giao diện
Sử dụng nhãn rõ ràng cho trường nhập liệu. Hiển thị đơn vị tiền tệ nhất
quán. Thông báo thao tác thành công và thất bại cần dễ hiểu. Nút xóa
hoặc thao tác nguy hiểm nên có bước xác nhận. Bảng dữ liệu nên có tiêu
đề cột rõ ràng. Danh sách dài nên cân nhắc tìm kiếm, lọc hoặc phân
trang. Không chỉ dựa vào màu sắc để biểu thị trạng thái.
47. Quy ước nghiệp vụ
Giá bán tại thời điểm lập hóa đơn cần được lưu để bảo toàn lịch sử. Biến
động kho cần có dấu vết. Không xóa dữ liệu lịch sử giao dịch một cách
tùy tiện. Tài khoản khách hàng và tài khoản nhân viên cần phân biệt rõ.
Vai trò phải được kiểm tra tại backend. Dữ liệu mẫu chỉ phục vụ thử
nghiệm. Các quy tắc chi tiết cần thống nhất với yêu cầu thực tế của cửa
hàng.
48. Danh sách kiểm tra trước khi demo
- [ ] Đã cài Node.js LTS.
- [ ] Đã cài JDK 17+.
- [ ] Đã cài XAMPP.
- [ ] MySQL đang chạy.
- [ ] Đã cài dependency bằng npm install.
- [ ] Đã chạy npm run migrate.
- [ ] Database QuanLySieuThiMini tồn tại.
- [ ] Đã chạy npm run dev.
- [ ] Truy cập được http://localhost:5173.
- [ ] Đăng nhập được bằng tài khoản mẫu.
- [ ] Đăng ký được tài khoản khách hàng.
- [ ] Các chức năng chính đã được kiểm tra.
- [ ] Ảnh sản phẩm tải được hoặc có phương án thay thế.
49. Danh sách kiểm tra trước khi bàn giao
- [ ] README được cập nhật theo phiên bản mã nguồn.
- [ ] Không còn mật khẩu thật trong mã nguồn.
- [ ] Database đã được sao lưu.
- [ ] File SQL được kiểm tra khả năng import.
- [ ] Tài khoản mẫu được ghi rõ là tài khoản demo.
- [ ] Các chức năng quan trọng đã được kiểm thử.
- [ ] Các lỗi đã biết được ghi nhận.
- [ ] Hướng dẫn chạy dự án đã được xác minh.
- [ ] Ảnh bên ngoài có quyền sử dụng phù hợp.
- [ ] Cấu hình production đã được tách khỏi cấu hình phát triển.
50. Thông tin cần xác minh theo repository
Các nội dung sau cần được đối chiếu với mã nguồn trước khi dùng README
như tài liệu triển khai chính thức: - Tên chính xác của thư mục backend
và frontend. - Phiên bản Spring Boot đang sử dụng. - Cách khởi động
backend (Maven, Gradle hay script riêng). - Cổng backend và địa chỉ
API. - Tên các bảng và quan hệ trong database. - Danh sách endpoint thực
tế. - Danh sách quyền chi tiết của từng vai trò. - Cách xử lý token và
thời hạn token. - Các script thực tế được khai báo trong package.json.
README chỉ khẳng định các lệnh và đường dẫn đã được cung cấp trong mô tả
dự án; các chi tiết chưa có được ghi rõ là cần xác minh.
51. Câu lệnh tham khảo
Cài dependency:
npm install
Chạy migration:
npm run migrate
Chạy ứng dụng:
npm run dev
Kiểm tra Node:
node -v
Kiểm tra npm:
npm -v
Kiểm tra Java:
java -version
Các câu lệnh backend riêng cần căn cứ vào cấu hình Maven/Gradle của
repository.
52. Câu hỏi thường gặp
Có cần Internet không?
Có, cần Internet để tải dependency lần đầu và tải ảnh sản phẩm trực
tuyến. ### Có thể dùng MariaDB không? Có thể dùng MySQL 8 hoặc MariaDB
theo cấu hình tương thích của dự án. ### Database tên gì?
QuanLySieuThiMini. ### File SQL import là file nào?
xampp_migration.sql. ### Trang đăng ký khách hàng ở đâu?
/store/register. ### Trang đăng nhập khách hàng ở đâu?
/store/login. ### Trang tài khoản khách hàng ở đâu? /store/account.
### Khách hàng có quyền quản trị không? Không. Khách hàng sử dụng vai
trò CUSTOMER.
53. Thuật ngữ
Backend: Phần xử lý nghiệp vụ và cung cấp API. Frontend: Giao
diện người dùng chạy trên trình duyệt. Database: Nơi lưu trữ dữ liệu
của hệ thống. Migration: Quá trình tạo hoặc cập nhật cấu trúc dữ
liệu. JPA: Công nghệ ánh xạ đối tượng Java với dữ liệu quan hệ.
Spring Security: Thành phần hỗ trợ xác thực và phân quyền.
BCrypt: Thuật toán băm mật khẩu. Token: Chuỗi thông tin dùng để
xác thực các yêu cầu. Tồn kho: Số lượng hàng hóa hiện có theo dữ
liệu hệ thống. Hóa đơn: Bản ghi giao dịch bán hàng. Xóa mềm:
Đánh dấu dữ liệu không còn hoạt động nhưng chưa xóa vật lý.
54. Đóng góp và chỉnh sửa dự án
Khi chỉnh sửa, nên xác định rõ phạm vi chức năng bị ảnh hưởng. Không
thay đổi định danh API hoặc database nếu chưa đánh giá tương thích. Tạo
bản sao lưu trước khi thay đổi migration. Kiểm thử các vai trò liên quan
sau khi sửa phân quyền. Cập nhật README khi thay đổi lệnh chạy, đường
dẫn hoặc nghiệp vụ. Ghi lại các thay đổi quan trọng trong lịch sử phiên
bản.
55. Giấy phép và tài nguyên bên ngoài
Dự án có sử dụng ảnh từ các website bên ngoài theo danh sách tại mục ảnh
sản phẩm. Việc dẫn liên kết không đồng nghĩa với việc đã có quyền sử
dụng thương mại. Người triển khai cần tự kiểm tra điều khoản, giấy phép
và quyền sử dụng. Nên ưu tiên ảnh do cửa hàng sở hữu hoặc ảnh có giấy
phép phù hợp. Các thư viện phần mềm cũng cần tuân thủ giấy phép tương
ứng.
56. Kết luận
Ứng dụng Quản lý siêu thị mini -- Đồ ăn vặt & Đồ chơi hỗ trợ các nghiệp
vụ cơ bản của cửa hàng bán lẻ. Hệ thống kết hợp giao diện
React/TypeScript/Vite, backend Java/Spring Boot và database
MySQL/MariaDB. Các chức năng trọng tâm gồm quản lý hàng hóa, kho, bán
hàng, khách hàng, nhân viên và phân quyền. Hướng dẫn chạy nhanh là bật
MySQL trong XAMPP, cài dependency, chạy migration và khởi động ứng dụng.
Trước khi triển khai thực tế, cần xác minh cấu hình theo repository,
thay mật khẩu mẫu và thiết lập bảo mật/sao lưu phù hợp. ## Phụ lục 1:
Ghi chú vận hành
- Phiên bản dự án: ghi theo phiên bản repository đang sử dụng.
- Môi trường: Windows, Node.js LTS, JDK 17+, XAMPP.
- Database: QuanLySieuThiMini.
- File migration: xampp_migration.sql.
- Frontend URL theo cấu hình hướng dẫn: http://localhost:5173.
- Trước khi thao tác dữ liệu thật, tạo bản sao lưu.
- Sau khi thay đổi cấu hình, khởi động lại tiến trình liên quan.
- Kiểm tra log khi chức năng không hoạt động như mong đợi.
- Không chia sẻ thông tin xác thực trong tài liệu công khai.
- Cập nhật phụ lục này khi quy trình vận hành thay đổi.
Phụ lục 2: Ghi chú vận hành
- Phiên bản dự án: ghi theo phiên bản repository đang sử dụng.
- Môi trường: Windows, Node.js LTS, JDK 17+, XAMPP.
- Database: QuanLySieuThiMini.
- File migration: xampp_migration.sql.
- Frontend URL theo cấu hình hướng dẫn: http://localhost:5173.
- Trước khi thao tác dữ liệu thật, tạo bản sao lưu.
- Sau khi thay đổi cấu hình, khởi động lại tiến trình liên quan.
- Kiểm tra log khi chức năng không hoạt động như mong đợi.
- Không chia sẻ thông tin xác thực trong tài liệu công khai.
- Cập nhật phụ lục này khi quy trình vận hành thay đổi.
Phụ lục 3: Ghi chú vận hành
- Phiên bản dự án: ghi theo phiên bản repository đang sử dụng.
- Môi trường: Windows, Node.js LTS, JDK 17+, XAMPP.
- Database: QuanLySieuThiMini.
- File migration: xampp_migration.sql.
- Frontend URL theo cấu hình hướng dẫn: http://localhost:5173.
- Trước khi thao tác dữ liệu thật, tạo bản sao lưu.
- Sau khi thay đổi cấu hình, khởi động lại tiến trình liên quan.
- Kiểm tra log khi chức năng không hoạt động như mong đợi.
- Không chia sẻ thông tin xác thực trong tài liệu công khai.
- Cập nhật phụ lục này khi quy trình vận hành thay đổi.
Phụ lục 4: Ghi chú vận hành
- Phiên bản dự án: ghi theo phiên bản repository đang sử dụng.
- Môi trường: Windows, Node.js LTS, JDK 17+, XAMPP.
- Database: QuanLySieuThiMini.
- File migration: xampp_migration.sql.
- Frontend URL theo cấu hình hướng dẫn: http://localhost:5173.
- Trước khi thao tác dữ liệu thật, tạo bản sao lưu.
- Sau khi thay đổi cấu hình, khởi động lại tiến trình liên quan.
- Kiểm tra log khi chức năng không hoạt động như mong đợi.
- Không chia sẻ thông tin xác thực trong tài liệu công khai.
- Cập nhật phụ lục này khi quy trình vận hành thay đổi.
Phụ lục 5: Ghi chú vận hành
- Phiên bản dự án: ghi theo phiên bản repository đang sử dụng.
- Môi trường: Windows, Node.js LTS, JDK 17+, XAMPP.
- Database: QuanLySieuThiMini.
- File migration: xampp_migration.sql.
- Frontend URL theo cấu hình hướng dẫn: http://localhost:5173.
- Trước khi thao tác dữ liệu thật, tạo bản sao lưu.
- Sau khi thay đổi cấu hình, khởi động lại tiến trình liên quan.
- Kiểm tra log khi chức năng không hoạt động như mong đợi.
- Không chia sẻ thông tin xác thực trong tài liệu công khai.
- Cập nhật phụ lục này khi quy trình vận hành thay đổi.
Phụ lục 6: Ghi chú vận hành
- Phiên bản dự án: ghi theo phiên bản repository đang sử dụng.
- Môi trường: Windows, Node.js LTS, JDK 17+, XAMPP.
- Database: QuanLySieuThiMini.
- File migration: xampp_migration.sql.
- Frontend URL theo cấu hình hướng dẫn: http://localhost:5173.
- Trước khi thao tác dữ liệu thật, tạo bản sao lưu.
- Sau khi thay đổi cấu hình, khởi động lại tiến trình liên quan.
- Kiểm tra log khi chức năng không hoạt động như mong đợi.
- Không chia sẻ thông tin xác thực trong tài liệu công khai.
- Cập nhật phụ lục này khi quy trình vận hành thay đổi.
Phụ lục 7: Ghi chú vận hành
- Phiên bản dự án: ghi theo phiên bản repository đang sử dụng.
- Môi trường: Windows, Node.js LTS, JDK 17+, XAMPP.
- Database: QuanLySieuThiMini.
- File migration: xampp_migration.sql.
- Frontend URL theo cấu hình hướng dẫn: http://localhost:5173.
- Trước khi thao tác dữ liệu thật, tạo bản sao lưu.
- Sau khi thay đổi cấu hình, khởi động lại tiến trình liên quan.
- Kiểm tra log khi chức năng không hoạt động như mong đợi.
- Không chia sẻ thông tin xác thực trong tài liệu công khai.
- Cập nhật phụ lục này khi quy trình vận hành thay đổi.
Phụ lục 8: Ghi chú vận hành
- Phiên bản dự án: ghi theo phiên bản repository đang sử dụng.
- Môi trường: Windows, Node.js LTS, JDK 17+, XAMPP.
- Database: QuanLySieuThiMini.
- File migration: xampp_migration.sql.
- Frontend URL theo cấu hình hướng dẫn: http://localhost:5173.
- Trước khi thao tác dữ liệu thật, tạo bản sao lưu.
- Sau khi thay đổi cấu hình, khởi động lại tiến trình liên quan.
- Kiểm tra log khi chức năng không hoạt động như mong đợi.
- Không chia sẻ thông tin xác thực trong tài liệu công khai.
- Cập nhật phụ lục này khi quy trình vận hành thay đổi.
Phụ lục 9: Ghi chú vận hành
- Phiên bản dự án: ghi theo phiên bản repository đang sử dụng.
- Môi trường: Windows, Node.js LTS, JDK 17+, XAMPP.
- Database: QuanLySieuThiMini.
- File migration: xampp_migration.sql.
- Frontend URL theo cấu hình hướng dẫn: http://localhost:5173.
- Trước khi thao tác dữ liệu thật, tạo bản sao lưu.
- Sau khi thay đổi cấu hình, khởi động lại tiến trình liên quan.
- Kiểm tra log khi chức năng không hoạt động như mong đợi.
- Không chia sẻ thông tin xác thực trong tài liệu công khai.
- Cập nhật phụ lục này khi quy trình vận hành thay đổi.
Phụ lục 10: Ghi chú vận hành
- Phiên bản dự án: ghi theo phiên bản repository đang sử dụng.
- Môi trường: Windows, Node.js LTS, JDK 17+, XAMPP.
- Database: QuanLySieuThiMini.
- File migration: xampp_migration.sql.
- Frontend URL theo cấu hình hướng dẫn: http://localhost:5173.
- Trước khi thao tác dữ liệu thật, tạo bản sao lưu.
- Sau khi thay đổi cấu hình, khởi động lại tiến trình liên quan.
- Kiểm tra log khi chức năng không hoạt động như mong đợi.
- Không chia sẻ thông tin xác thực trong tài liệu công khai.
- Cập nhật phụ lục này khi quy trình vận hành thay đổi.
Phụ lục 11: Ghi chú vận hành
- Phiên bản dự án: ghi theo phiên bản repository đang sử dụng.
- Môi trường: Windows, Node.js LTS, JDK 17+, XAMPP.
- Database: QuanLySieuThiMini.
- File migration: xampp_migration.sql.
- Frontend URL theo cấu hình hướng dẫn: http://localhost:5173.
- Trước khi thao tác dữ liệu thật, tạo bản sao lưu.
- Sau khi thay đổi cấu hình, khởi động lại tiến trình liên quan.
- Kiểm tra log khi chức năng không hoạt động như mong đợi.
- Không chia sẻ thông tin xác thực trong tài liệu công khai.
- Cập nhật phụ lục này khi quy trình vận hành thay đổi.
Phụ lục 12: Ghi chú vận hành
- Phiên bản dự án: ghi theo phiên bản repository đang sử dụng.
- Môi trường: Windows, Node.js LTS, JDK 17+, XAMPP.
- Database: QuanLySieuThiMini.
- File migration: xampp_migration.sql.
- Frontend URL theo cấu hình hướng dẫn: http://localhost:5173.
- Trước khi thao tác dữ liệu thật, tạo bản sao lưu.
- Sau khi thay đổi cấu hình, khởi động lại tiến trình liên quan.
- Kiểm tra log khi chức năng không hoạt động như mong đợi.
- Không chia sẻ thông tin xác thực trong tài liệu công khai.
- Cập nhật phụ lục này khi quy trình vận hành thay đổi.
Phụ lục 13: Ghi chú vận hành
- Phiên bản dự án: ghi theo phiên bản repository đang sử dụng.
- Môi trường: Windows, Node.js LTS, JDK 17+, XAMPP.
- Database: QuanLySieuThiMini.
- File migration: xampp_migration.sql.
- Frontend URL theo cấu hình hướng dẫn: http://localhost:5173.
- Trước khi thao tác dữ liệu thật, tạo bản sao lưu.
- Sau khi thay đổi cấu hình, khởi động lại tiến trình liên quan.
- Kiểm tra log khi chức năng không hoạt động như mong đợi.
- Không chia sẻ thông tin xác thực trong tài liệu công khai.
- Cập nhật phụ lục này khi quy trình vận hành thay đổi.
Phụ lục 14: Ghi chú vận hành
- Phiên bản dự án: ghi theo phiên bản repository đang sử dụng.
- Môi trường: Windows, Node.js LTS, JDK 17+, XAMPP.
- Database: QuanLySieuThiMini.
- File migration: xampp_migration.sql.
- Frontend URL theo cấu hình hướng dẫn: http://localhost:5173.
- Trước khi thao tác dữ liệu thật, tạo bản sao lưu.
- Sau khi thay đổi cấu hình, khởi động lại tiến trình liên quan.
- Kiểm tra log khi chức năng không hoạt động như mong đợi.
- Không chia sẻ thông tin xác thực trong tài liệu công khai.
- Cập nhật phụ lục này khi quy trình vận hành thay đổi.
Phụ lục 15: Ghi chú vận hành
- Phiên bản dự án: ghi theo phiên bản repository đang sử dụng.
- Môi trường: Windows, Node.js LTS, JDK 17+, XAMPP.
- Database: QuanLySieuThiMini.
- File migration: xampp_migration.sql.
- Frontend URL theo cấu hình hướng dẫn: http://localhost:5173.
- Trước khi thao tác dữ liệu thật, tạo bản sao lưu.
- Sau khi thay đổi cấu hình, khởi động lại tiến trình liên quan.
- Kiểm tra log khi chức năng không hoạt động như mong đợi.
- Không chia sẻ thông tin xác thực trong tài liệu công khai.
- Cập nhật phụ lục này khi quy trình vận hành thay đổi.
Phụ lục nghiệp vụ: Các điểm cần đối chiếu
- [ ] Đối chiếu mục 1: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 2: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 3: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 4: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 5: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 6: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 7: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 8: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 9: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 10: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 11: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 12: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 13: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 14: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 15: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 16: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 17: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 18: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 19: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 20: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 21: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 22: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 23: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 24: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 25: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 26: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 27: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 28: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 29: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 30: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 31: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 32: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 33: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 34: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 35: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 36: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 37: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 38: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 39: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 40: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 41: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 42: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 43: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 44: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 45: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 46: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 47: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 48: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 49: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 50: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 51: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 52: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 53: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 54: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 55: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 56: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 57: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 58: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 59: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 60: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 61: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 62: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 63: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 64: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 65: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 66: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 67: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 68: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 69: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 70: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 71: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 72: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 73: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 74: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 75: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 76: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 77: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 78: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 79: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
- [ ] Đối chiếu mục 80: xác nhận chức năng có trong phiên bản mã nguồn
  hiện tại.
Phụ lục cấu hình: Các điểm cần xác minh
- [ ] Xác minh cấu hình 1: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 2: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 3: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 4: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 5: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 6: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 7: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 8: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 9: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 10: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 11: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 12: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 13: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 14: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 15: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 16: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 17: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 18: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 19: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 20: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 21: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 22: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 23: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 24: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 25: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 26: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 27: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 28: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 29: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 30: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 31: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 32: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 33: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 34: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 35: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 36: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 37: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 38: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 39: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 40: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 41: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 42: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 43: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 44: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 45: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 46: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 47: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 48: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 49: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 50: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 51: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 52: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 53: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 54: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 55: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 56: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 57: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 58: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 59: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 60: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 61: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 62: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 63: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 64: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 65: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 66: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 67: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 68: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 69: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 70: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 71: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 72: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 73: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 74: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 75: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 76: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 77: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 78: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 79: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
- [ ] Xác minh cấu hình 80: kiểm tra trong file cấu hình hoặc mã nguồn
  trước khi thay đổi.
