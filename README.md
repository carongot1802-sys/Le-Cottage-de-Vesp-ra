# Le Cottage de Vespéra - bản chạy trên GitHub Pages

## Cấu trúc
- `index.html`: trang web cho khách quán đọc (ai cũng xem được, không cần đăng nhập). Khi mở web sẽ hiện một lá thư chào, gõ cửa xong mới vào mục Chào mừng, tiếp theo là Bài viết và À propos
- `admin.html`: trang quản trị của cô chủ cottage (đăng bài, ảnh, video, câu hàng ngày, trang Chào mừng, giao diện, liên hệ, À propos)
- `data/posts.json`, `data/site.json`: nơi lưu bài viết và cài đặt (admin tự cập nhật, bạn không cần mở)
- `media/`: thư mục ảnh/video, tự tạo khi bạn upload lần đầu

## Cài đặt (làm 1 lần)
1. Tạo repo **public** mới trên GitHub (vd `le-cottage`).
2. Bấm **Add file → Upload files**, kéo cả thư mục này vào (giữ nguyên thư mục `data`), bấm **Commit changes**.
3. Vào **Settings → Pages**, mục Build and deployment chọn **Deploy from a branch**, branch `main`, thư mục `/ (root)`, bấm Save.
4. Chờ ~1 phút, web chạy ở `https://TENBAN.github.io/le-cottage/`.

## Tạo token để đăng bài
1. GitHub → avatar → **Settings → Developer settings → Personal access tokens → Fine-grained tokens → Generate new token**.
2. **Repository access**: chọn *Only select repositories* → chọn repo của bạn.
3. **Permissions → Repository permissions → Contents**: chọn **Read and write**.
4. Tạo xong, copy token (chỉ hiện 1 lần).

## Đăng bài
1. Mở `https://TENBAN.github.io/le-cottage/admin.html`.
2. Điền repo (thường tự điền sẵn) và dán token, bấm **Kết nối**. Token chỉ lưu trong trình duyệt của bạn.
3. Viết bài, thêm ảnh/video, bấm **Đăng bài**. Web cập nhật sau khoảng 1 phút.

## Trang Chào mừng và hoa iris
- Mục Chào mừng hiện đầu tiên khi khách quán mở web: hoa iris tím, tiêu đề, lời chào, lời nhắn, hình ao sen có chú ếch nhảy, và số iris cottage đã nhận.
- Muốn đổi chữ, vào admin, tab **Chào mừng**, sửa rồi bấm **Lưu trang chào mừng** (có cả bản tiếng Việt và tiếng Pháp). Trong đó có cả dòng đếm iris, lời mời và lời cảm ơn ở cuối bài. Ghi `{n}` ở chỗ muốn hiện con số.
- Cuối mỗi bài có một bông iris tím. Khách bấm vào thì cottage được thêm một iris, mỗi khách chỉ tặng được một bông cho mỗi bài (trình duyệt tự nhớ).
- Số iris được lưu bằng dịch vụ đếm miễn phí bên ngoài (abacus.jasoncameron.dev), vì GitHub Pages không tự lưu được lượt bấm của khách. Admin hiện tổng iris ở tab Chào mừng và số iris của từng bài ở tab Bài viết.
- Nếu một ngày dịch vụ đếm ngừng hoạt động, web vẫn chạy bình thường, chỉ là khung đếm iris sẽ ẩn đi. Khi đó bạn có thể thêm khóa `"iris": {"api": "địa chỉ dịch vụ khác"}` vào `data/site.json`.
- Số iris gắn với địa chỉ web. Nếu đổi tên repo hoặc đổi tên miền thì bộ đếm sẽ bắt đầu lại từ 0.

## Lá thư chào và nút Mời thưởng trà
- Mỗi khi khách mở web sẽ thấy một lá thư cũ có in chìm hoa iris: "Chào mừng đến Cottage của tôi, chúc một ngày tốt lành". Khách bấm dòng **Mời gõ cửa** (hoặc phím Esc) để đóng thư và vào trang Chào mừng.
- Nếu khách mở thẳng link một bài viết hoặc trang Giới thiệu, thư vẫn hiện nhưng đóng xong khách ở lại đúng trang họ cần.
- Dưới khung đếm iris ở trang Chào mừng có nút xanh lá **Mời thưởng trà**, bấm vào sẽ chuyển sang mục Bài viết.
- Muốn đổi chữ trên lá thư hoặc nút, sửa trong `index.html`, các khóa `lw`, `lk` (thư) và `tea` (nút) ở đối tượng `T`.

## Câu hàng ngày
- Ở đầu trang Bài viết, phía trên danh sách bài, có một khung hiện câu quote hoặc expression của hôm nay.
- Mỗi ngày vào admin, tab **Câu hàng ngày**, gõ câu (có ô giải nghĩa, có cả bản tiếng Việt và tiếng Pháp), chọn ngày rồi bấm **Lưu câu hôm nay**. Web cập nhật sau khoảng 1 phút.
- Để trống cả hai ngôn ngữ thì khung tự ẩn. Câu được lưu trong `data/site.json`, khóa `quote`.

## Bài trước và bài kế tiếp
- Cuối mỗi bài có hai ô gợi ý: bài đăng trước đó (cũ hơn) bên trái và bài đăng kế tiếp (mới hơn) bên phải. Bài đầu hoặc bài mới nhất thì chỉ hiện một ô.

## Lưu ý
- Ai cũng mở được `admin.html` nhưng không có token thì không làm gì được. Đừng chia sẻ token. Nếu lộ, xóa token trên GitHub rồi tạo cái mới.
- Mỗi file ảnh/video tối đa 40 MB, video nên dưới 25 MB. Video dài nên nén trước hoặc đăng lên YouTube.
- Xóa bài chỉ gỡ bài khỏi web, file ảnh vẫn nằm trong `media/`.
- Phần Học vấn, Kinh nghiệm, Giải thưởng sửa trong admin, tab **À propos**.
- Biểu tượng của web nay là hoa iris tím (trên tab trình duyệt và trang chào mừng) và fleur-de-lis vàng (ở các điểm trang trí). Các nút chức năng như mũi tên quay lại hay dấu đóng ảnh vẫn giữ nguyên.
- Mở trực tiếp file bằng cách nhấp đúp trên máy sẽ không hiện bài vì trình duyệt chặn đọc dữ liệu. Hãy xem qua link GitHub Pages.
