# Le Cottage de Vespéra - bản chạy trên GitHub Pages

## Cấu trúc
- `index.html`: trang web cho khách quán đọc (ai cũng xem được, không cần đăng nhập). Khi mở web sẽ hiện tấm thiệp chào, gõ cửa xong mới vào mục Chào mừng, tiếp theo là Bài viết và À propos
- `admin.html`: trang quản trị của cô chủ cottage (đăng bài, ảnh, video, câu hàng ngày, trang Chào mừng, thư chào, giao diện và bộ theme, liên hệ, À propos)
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
3. Tab **Bài viết** → **Viết bài mới**, soạn xong bấm **Đăng bài**. Web cập nhật sau khoảng 1 phút.

### Cấu trúc một bài
- **Title**, **Chủ đề**, **Chapeau** (đoạn dẫn ngắn dưới tiêu đề), mỗi mục có ô tiếng Việt và tiếng Pháp (bỏ trống bên nào thì web dùng bên còn lại). **Ảnh bìa** chỉ dùng cho danh sách bài, bỏ trống thì web lấy ảnh đầu tiên trong bài.
- **Nội dung** gồm các "khối" xếp nối nhau, thêm bao nhiêu cũng được:
  - **＋ Subtitle**: tiêu đề phụ cho từng phần của bài.
  - **＋ Đoạn văn**: cách 1 dòng trống để sang đoạn mới. Có thể dùng `**chữ đậm**`, `*chữ nghiêng*`, `[chữ hiện ra](https://link)`.
  - **＋ Ảnh**: chọn được nhiều ảnh một lúc, mỗi ảnh một khối kèm ô **chú thích chân ảnh** (VI/FR). Ảnh lớn được tự thu nhỏ trước khi tải lên. Khách bấm vào ảnh để xem phóng to.
  - **＋ Video**: tải file video lên (mỗi file tối đa 40 MB, nên dưới 25 MB), cũng có chú thích.
  - **＋ Video YouTube/Vimeo**: dán link, web tự nhúng khung video. Hợp với video dài.
- Khối mới được chèn ngay sau khối bạn đang soạn (hoặc xuống cuối bài nếu chưa chọn khối nào). Dùng nút ↑ ↓ để đổi thứ tự, ✕ để xóa khối.
- Bài cũ (kiểu trước đây, một ô nội dung + ảnh gộp) vẫn hiện bình thường. Khi bấm Sửa, bài được tự chuyển sang dạng khối để bạn chỉnh tiếp.

## Trang Chào mừng và hoa iris
- Mục Chào mừng hiện đầu tiên khi khách quán mở web: hoa iris, tiêu đề, lời chào, lời nhắn, khung video 16:9, và số iris cottage đã nhận.
- Muốn đổi chữ, vào admin, tab **Chào mừng**, sửa rồi bấm **Lưu trang chào mừng** (có cả bản tiếng Việt và tiếng Pháp). Trong đó có cả dòng đếm iris, lời mời và lời cảm ơn ở cuối bài. Ghi `{n}` ở chỗ muốn hiện con số.
- Cuối mỗi bài có một bông iris tím. Khách bấm vào thì cottage được thêm một iris, mỗi khách chỉ tặng được một bông cho mỗi bài (trình duyệt tự nhớ).
- Số iris được lưu bằng dịch vụ đếm miễn phí bên ngoài (abacus.jasoncameron.dev), vì GitHub Pages không tự lưu được lượt bấm của khách. Admin hiện tổng iris ở tab Chào mừng và số iris của từng bài ở tab Bài viết.
- Nếu một ngày dịch vụ đếm ngừng hoạt động, web vẫn chạy bình thường, chỉ là khung đếm iris sẽ ẩn đi. Khi đó bạn có thể thêm khóa `"iris": {"api": "địa chỉ dịch vụ khác"}` vào `data/site.json`.
- Số iris gắn với địa chỉ web. Nếu đổi tên repo hoặc đổi tên miền thì bộ đếm sẽ bắt đầu lại từ 0.

## Món mời thưởng trà (random)
- Admin có thể thêm danh sách món (tên Tiếng Việt + Français + ảnh) trong tab "Chào mừng" → phần "Món mời thưởng trà (quản lý)".
- Khi khách bấm nút "Mời thưởng trà" trên trang Chào mừng, web sẽ chọn ngẫu nhiên một món từ danh sách và hiện ảnh + tên (theo ngôn ngữ đang chọn). Khách sau đó bấm "Xem bài" để vào trang Bài viết.
- Ảnh món được lưu trong thư mục `media/` khi bạn upload từ admin.
- Lưu ý: nếu danh sách trống, nút sẽ chuyển khách sang trang Bài viết như trước.

## Icon rơi nền (drift icons)
- Admin có thể upload nhiều icon (PNG nền trong khuyến khích) trong tab "Chào mừng" → phần "Icon rơi nền (drift)".
- Bật/tắt hiệu ứng rơi toàn trang từ admin. Khi bật, client sẽ vẽ các icon rơi nhẹ theo animation (tương tự hiệu ứng tuyết). Mỗi file icon được lưu vào `media/` và đường dẫn lưu trong `data/site.json` (site.design.driftIcons).
- Lưu ý: tôi giới hạn số phần tử DOM (mặc định tối đa 20) để tránh giật trang. Nếu muốn nhiều hơn hoặc khác, chỉnh code `renderDrift()` trong `index.html`.

## Menu 3 gạch
- Ba mục Chào mừng, Bài viết, Giới thiệu nay ẩn trong biểu tượng 3 gạch ở góc trên bên trái. Bấm vào thì menu trượt ra, bấm mục nào, bấm ra ngoài vùng menu, bấm dấu ✕ hoặc phím Esc đều đóng lại.

## Giao diện và Bộ theme (tab Giao diện trong admin)
- Đổi được: hình, màu và độ phủ của **header** (kèm màu chữ và đường kẻ dưới header), hình và màu **chân trang** (khối Contact + dòng ©), màu và hình **nền trang**, **màu nhấn** (tiêu đề, nút, chữ chủ đề) và **màu phụ** (chữ xanh). Khung "Xem trước" ở đầu tab cho bạn thấy ngay kết quả.
- Màu nhấn và màu phụ áp dụng cả khi khách dùng chế độ tối, nên chọn màu đủ đậm hoặc đủ sáng cho dễ đọc. Mục nào có nút "Về mặc định" thì bấm để quay lại màu gốc.
- **Chế độ sáng và tối**: ở góc phải header có nút trăng/mặt trời để khách đổi giữa hai chế độ (nút này ẩn đi nếu theme đang chạy có khóa chế độ). Lần đầu vào web, chế độ theo máy của khách, sau đó web nhớ lựa chọn của họ. Màu nền và màu chữ bạn đặt trong Giao diện mặc định chỉ dùng ở chế độ sáng cho chế độ tối luôn dễ đọc. Màu nền riêng cho chế độ tối chọn ở mục **Màu nền chế độ tối**, bỏ trống thì dùng nền tối mặc định.
- **Độ đậm hình nền trang** nay chỉnh được tới 80% (trước đây tối đa 60%). Ở chế độ tối, hình nền tự được làm dịu bớt để không chói.
- **Trang Chào mừng (chữ và biểu tượng)**: đổi được biểu tượng lớn ở đầu trang (thay hoa iris tím bằng hình khác, nên là PNG nền trong, vd bông tuyết cho theme Giáng sinh) và chỉnh cỡ của nó, chọn phông chữ cho tiêu đề và cho lời chào, lời nhắn, chọn màu chữ riêng cho tiêu đề, lời chào, lời nhắn. Bấm "Về hoa iris mặc định" để quay lại hoa tím.
- **Trang Giới thiệu (chữ)**: chọn phông chữ và màu chữ cho tiêu đề và cho nội dung.
- Mỗi nhóm màu chữ có ô **Dùng các màu chữ này cả ở chế độ tối**. Để trống thì chế độ tối dùng màu chữ tối mặc định. Phông chữ thì áp dụng ở cả hai chế độ. Các phông có sẵn đều hỗ trợ tiếng Việt: Chantelli Antiqua, Playfair Display, Cormorant Garamond, Lora, Dancing Script, Montserrat, Be Vietnam Pro.
- **Khóa chế độ sáng/tối** (mục cùng tên trong tab Giao diện): chọn **Luôn tối** hoặc **Luôn sáng** thì web hiện đúng một chế độ cho mọi khách và nút trăng/mặt trời ở header được ẩn đi. Khi khóa, các màu bạn chọn (màu nền trang, màu chữ trang Chào mừng và Giới thiệu) áp dụng thẳng cho chế độ đã khóa, không cần tích ô "Dùng các màu chữ này cả ở chế độ tối" và không cần chọn riêng màu nền chế độ tối (để trống ô đó thì web dùng Màu nền trang). Ví dụ theme Halloween: chọn Luôn tối, rồi chọn màu cam cháy, tím sáng cho tiêu đề và lời chào mà không phải lo màu có đọc được ở chế độ sáng hay không. Lựa chọn khóa được lưu cùng từng theme, nên Halloween luôn tối còn theme thường vẫn để khách tự chọn.
- Tất cả các mục mới trên đều được lưu cùng **Bộ theme**, nên mỗi theme có thể có biểu tượng, phông và màu chữ riêng.
- **Bộ theme**: chỉnh Giao diện và Thư chào ưng ý rồi gõ tên (vd "Giáng sinh 2026"), bấm "Lưu cấu hình hiện tại thành theme". Khi có sự kiện, chỉ cần bấm **Áp dụng và đăng** ở theme tương ứng là cả header, chân trang, màu sắc và thư chào đổi cùng lúc. Theme chỉ lưu đường dẫn ảnh nên không làm nặng web.
- Lưu ý: Áp dụng theme sẽ ghi đè Giao diện và Thư chào đang chạy. Nếu muốn giữ lại bộ hiện tại, hãy lưu nó thành một theme trước.

## Video ở trang Chào mừng
- Khung video tỉ lệ 16:9 nằm ngay dưới lời nhắn. Để thêm video: vào repo GitHub, tạo thư mục `media` (nếu chưa có), upload file đặt tên đúng **`welcome.mp4`** vào đó (Add file → Upload files).
- Khi chưa có file, khung hiện chữ "Video sắp được đặt ở đây". Có file rồi thì khung tự đổi thành video.
- Video tự phát khi khách kéo xuống tới nơi, tự dừng khi kéo đi chỗ khác. Nếu khách chủ động bấm dừng thì web không tự phát lại nữa. Video phát ở chế độ tắt tiếng (trình duyệt bắt buộc mới cho tự phát), khách bật tiếng bằng nút loa trên thanh điều khiển.
- Nên dùng mp4 mã hóa H.264, dưới 25 MB. Muốn đổi tên hoặc đường dẫn file thì sửa `media/welcome.mp4` trong `index.html`.

## Thư chào (tab Thư chào trong admin)
- Đây là tấm thiệp hiện giữa màn hình khi khách vừa mở web. Bạn tự đổi mọi thứ trong admin, không cần sửa code:
  - **Hình thiệp**: bấm Chọn hình (ảnh vuông, dọc hay ngang đều được; ảnh lớn được tự thu nhỏ). Bấm "Về hình mặc định" để quay lại thiệp hoa tím có sẵn.
  - **Cách bấm để vào web**: nếu ảnh đã in sẵn chữ như "Mời gõ cửa !", chọn "Vùng bấm vô hình" rồi kéo 4 thanh trượt cho khung đỏ trong phần xem trước trùm đúng chữ đó. Nếu ảnh không có chữ nút, chọn "Nút chữ riêng", web sẽ vẽ thêm một nút với chữ (VI/FR) và màu bạn chọn.
  - **Màu phủ nền** sau thiệp và độ đậm, **độ bo góc**, bật/tắt **viền mảnh**.
  - **Hình rơi quanh thiệp**: hoa iris nhỏ (mặc định), hình của bạn (PNG nền trong, ví dụ bông tuyết, cánh mai), hoặc tắt hẳn.
  - Tắt ô "Hiện thư chào" nếu muốn khách vào thẳng web.
- Bấm vào chữ/nút, bấm vào thiệp hoặc phím Esc đều đóng thiệp. Nếu khách mở thẳng link một bài viết hoặc trang Giới thiệu, thiệp vẫn hiện nhưng đóng xong khách ở lại đúng trang họ cần.
- Sửa xong bấm **Lưu thư chào**, web cập nhật sau khoảng 1 phút. Thiệp mặc định là file `assets/thu-chao.jpg`.
- Dưới khung đếm iris ở trang Chào mừng có nút xanh lá **Mời thưởng trà**, bấm vào sẽ hiện món random nếu admin đã thêm; nếu chưa admin thêm nào thì nút chuyển thẳng sang trang Bài viết.

## Câu hàng ngày
- Ở đầu trang Bài viết, phía trên danh sách bài, có một khung hiện câu quote hoặc expression của hôm nay.
- Mỗi ngày vào admin, tab **Câu hàng ngày**, gõ câu (có ô giải nghĩa, có cả bản tiếng Việt và tiếng Pháp), chọn ngày rồi bấm **Lưu câu hôm nay**. Web cập nhật sau khoảng 1 phút.
- Để trống cả hai ngôn ngữ thì khung tự ẩn. Câu được lưu trong `data/site.json`, khóa `quote`.

## Bài trước và bài kế tiếp
- Cuối mỗi bài có hai ô gợi ý: bài đăng trước đó (cũ hơn) bên trái và bài đăng kế tiếp (mới hơn) bên phải. Bài đầu hoặc bài mới nhất thì chỉ hiện một ô.

## Lưu ý
- Ai cũng mở được `admin.html` nhưng không có token thì không làm gì được. Đừng chia sẻ token. Nếu lộ, xóa token trên GitHub rồi tạo cái mới.
- Mỗi file ảnh/video tối đa 40 MB, video nên dưới 25 MB. Video dài nên đăng lên YouTube rồi dùng khối "Video YouTube/Vimeo".
- Xóa bài chỉ gỡ bài khỏi web, file ảnh vẫn nằm trong `media/`.
- Phần Học vấn, Kinh nghiệm, Giải thưởng sửa trong admin, tab **À propos**.
- Biểu tượng của web dùng hình iris vẽ màu nước của bạn (trên tab trình duyệt, trang chào mừng, khung đếm iris và cuối mỗi bài).
- Mở trực tiếp file bằng cách nhấp đúp trên máy sẽ không hiện bài vì trình duyệt chặn đọc dữ liệu. Hãy xem qua link GitHub Pages.
