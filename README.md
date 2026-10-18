# Le Cottage de Vespéra - bản chạy trên GitHub Pages

## Cấu trúc
- `index.html`: trang web cho khách quán đọc (ai cũng xem được, không cần đăng nhập). Khi mở web sẽ hiện một lá thư chào, gõ cửa xong mới vào mục Chào mừng, tiếp theo là Bài viết và À propos
- `admin.html`: trang quản trị của cô chủ cottage (đăng bài, ảnh, video, câu hàng ngày, trang Chào mừng, giao diện, liên hệ, À propos)
- `assets/`: hai hình hoa iris (`iris-to.png` ở đầu trang Chào mừng, `iris-be.png` cho mọi iris nhỏ còn lại). Nhớ upload cả thư mục này lên GitHub
- `media/welcome.mp4`: video của trang Chào mừng (bạn tự thêm vào, xem phần bên dưới)
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
- Mục Chào mừng hiện đầu tiên khi khách quán mở web: hoa iris, tiêu đề, lời chào, lời nhắn, khung video 16:9, và số iris cottage đã nhận.
- Muốn đổi chữ, vào admin, tab **Chào mừng**, sửa rồi bấm **Lưu trang chào mừng** (có cả bản tiếng Việt và tiếng Pháp). Trong đó có cả dòng đếm iris, lời mời và lời cảm ơn ở cuối bài. Ghi `{n}` ở chỗ muốn hiện con số.
- Cuối mỗi bài có một bông iris tím. Khách bấm vào thì cottage được thêm một iris, mỗi khách chỉ tặng được một bông cho mỗi bài (trình duyệt tự nhớ).
- Số iris được lưu bằng dịch vụ đếm miễn phí bên ngoài (abacus.jasoncameron.dev), vì GitHub Pages không tự lưu được lượt bấm của khách. Admin hiện tổng iris ở tab Chào mừng và số iris của từng bài ở tab Bài viết.
- Nếu một ngày dịch vụ đếm ngừng hoạt động, web vẫn chạy bình thường, chỉ là khung đếm iris sẽ ẩn đi. Khi đó bạn có thể thêm khóa `"iris": {"api": "địa chỉ dịch vụ khác"}` vào `data/site.json`.
- Số iris gắn với địa chỉ web. Nếu đổi tên repo hoặc đổi tên miền thì bộ đếm sẽ bắt đầu lại từ 0.

## Menu 3 gạch
- Ba mục Chào mừng, Bài viết, Giới thiệu nay ẩn trong biểu tượng 3 gạch ở góc trên bên trái. Bấm vào thì menu trượt ra, bấm mục nào, bấm ra ngoài vùng menu, bấm dấu ✕ hoặc phím Esc đều đóng lại.

## Video ở trang Chào mừng
- Khung video tỉ lệ 16:9 nằm ngay dưới lời nhắn. Để thêm video: vào repo GitHub, tạo thư mục `media` (nếu chưa có), upload file đặt tên đúng **`welcome.mp4`** vào đó (Add file → Upload files).
- Khi chưa có file, khung hiện chữ "Video sắp được đặt ở đây". Có file rồi thì khung tự đổi thành video.
- Video tự phát khi khách kéo xuống tới nơi, tự dừng khi kéo đi chỗ khác. Nếu khách chủ động bấm dừng thì web không tự phát lại nữa. Video phát ở chế độ tắt tiếng (trình duyệt bắt buộc mới cho tự phát), khách bật tiếng bằng nút loa trên thanh điều khiển.
- Nên dùng mp4 mã hóa H.264, dưới 25 MB. Muốn đổi tên hoặc đường dẫn file thì sửa `media/welcome.mp4` trong `index.html`.

## Thiệp chào và nút Mời thưởng trà
- Mỗi khi khách mở web sẽ thấy tấm thiệp hoa tím (file `assets/thu-chao.jpg`) nổi lên giữa màn hình, nhẹ nhàng lơ lửng, vài bông iris nhỏ rơi chầm chậm xung quanh. Khách bấm vào chữ **Mời gõ cửa !** (hoặc bấm vào thiệp, hoặc phím Esc) để đóng thiệp và vào trang Chào mừng.
- Nếu khách mở thẳng link một bài viết hoặc trang Giới thiệu, thiệp vẫn hiện nhưng đóng xong khách ở lại đúng trang họ cần.
- Muốn đổi thiệp: làm ảnh vuông mới, đặt tên `thu-chao.jpg` rồi upload đè vào thư mục `assets`. Giữ chữ "Mời gõ cửa !" ở vị trí cũ (khoảng 2/3 chiều cao ảnh, giữa ảnh) vì nút bấm nằm chồng đúng chỗ đó.
- Chữ trên thiệp là chữ trong ảnh nên không đổi theo VI/FR.
- Dưới khung đếm iris ở trang Chào mừng có nút xanh lá **Mời thưởng trà**, bấm vào sẽ chuyển sang mục Bài viết. Chữ nút sửa trong `index.html`, khóa `tea` ở đối tượng `T`.

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
- Biểu tượng của web nay dùng hình iris vẽ màu nước của bạn (trên tab trình duyệt, trang chào mừng, lá thư, khung đếm iris và cuối mỗi bài) và fleur-de-lis vàng (ở các điểm trang trí). Các nút chức năng như mũi tên quay lại hay dấu đóng ảnh vẫn giữ nguyên.
- Mở trực tiếp file bằng cách nhấp đúp trên máy sẽ không hiện bài vì trình duyệt chặn đọc dữ liệu. Hãy xem qua link GitHub Pages.
