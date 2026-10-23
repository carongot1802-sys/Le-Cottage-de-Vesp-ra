# Le Cottage de Vespéra - bản chạy trên GitHub Pages

## Cấu trúc
- `index.html`: trang web cho khách quán đọc (ai cũng xem được, không cần đăng nhập). Khi mở web sẽ hiện tấm thiệp chào, gõ cửa xong mới vào mục Chào mừng, tiếp theo là Bài viết và À propos
- `admin.html`: trang quản trị của cô chủ cottage (đăng bài, ảnh, video, câu hàng ngày, bộ bài từ vựng Ngẫu nhiên, trang Chào mừng, món mời trà, gọi món, thư chào, giao diện và bộ theme, liên hệ, À propos)
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

## Thanh menu ở header
- Năm mục **Chào mừng**, **Bài viết**, **Ngẫu nhiên**, **Gọi món**, **Giới thiệu** nằm ngay trên dòng "Le Cottage de Vespéra" trong header, bấm mục nào là chuyển tới mục đó. Mục đang xem được gạch chân. Trên điện thoại thanh này tự xuống thành hai dòng. Chữ và màu của thanh menu đi theo "Màu chữ header" trong tab Giao diện. Muốn đổi tên một mục, sửa các khóa `nvw`, `navp`, `nva` (và `RN.vi.nav`, `RN.fr.nav` cho mục Ngẫu nhiên, `MN.vi.nav`, `MN.fr.nav` cho mục Gọi món) trong `index.html`.

## Giao diện và Bộ theme (tab Giao diện trong admin)
- Đổi được: hình, màu và độ phủ của **header** (kèm màu chữ và đường kẻ dưới header), hình và màu **chân trang** (khối Contact + dòng ©), màu và hình **nền trang**, **màu nhấn** (tiêu đề, nút, chữ chủ đề) và **màu phụ** (chữ xanh). Khung "Xem trước" ở đầu tab cho bạn thấy ngay kết quả.
- Màu nhấn và màu phụ áp dụng cả khi khách dùng chế độ tối, nên chọn màu đủ đậm hoặc đủ sáng cho dễ đọc. Mục nào có nút "Về mặc định" thì bấm để quay lại màu gốc.
- **Chế độ sáng và tối**: ở góc phải header có nút trăng/mặt trời để khách đổi giữa hai chế độ (nút này ẩn đi nếu theme đang chạy có khóa chế độ). Lần đầu vào web, chế độ theo máy của khách, sau đó web nhớ lựa chọn của họ. Màu nền và màu chữ bạn đặt trong Giao diện mặc định chỉ dùng ở chế độ sáng cho chế độ tối luôn dễ đọc. Màu nền riêng cho chế độ tối chọn ở mục **Màu nền chế độ tối**, bỏ trống thì dùng nền tối mặc định.
- **Độ đậm hình nền trang** nay chỉnh được tới 80% (trước đây tối đa 60%). Ở chế độ tối, hình nền tự được làm dịu bớt để không chói.
- **Trang Chào mừng (chữ và biểu tượng)**: đổi được biểu tượng lớn ở đầu trang (thay hoa iris tím bằng hình khác, nên là PNG nền trong, vd bông tuyết cho theme Giáng sinh) và chỉnh cỡ của nó, chọn phông chữ cho tiêu đề và cho lời chào, lời nhắn, chọn màu chữ riêng cho tiêu đề, lời chào, lời nhắn. Bấm "Về hoa iris mặc định" để quay lại hoa tím.
- **Trang Giới thiệu (chữ)**: chọn phông chữ và màu chữ cho tiêu đề và cho nội dung.
- Mỗi nhóm màu chữ có ô **Dùng các màu chữ này cả ở chế độ tối**. Để trống thì chế độ tối dùng màu chữ tối mặc định. Phông chữ thì áp dụng ở cả hai chế độ. Các phông có sẵn đều hỗ trợ tiếng Việt: Chantelli Antiqua, Playfair Display, Cormorant Garamond, Lora, Dancing Script, Montserrat, Be Vietnam Pro.
- **Khóa chế độ sáng/tối** (mục cùng tên trong tab Giao diện): chọn **Luôn tối** hoặc **Luôn sáng** thì web hiện đúng một chế độ cho mọi khách và nút trăng/mặt trời ở header được ẩn đi. Khi khóa, các màu bạn chọn (màu nền trang, màu chữ trang Chào mừng và Giới thiệu) áp dụng thẳng cho chế độ đã khóa, không cần tích ô "Dùng các màu chữ này cả ở chế độ tối" và không cần chọn riêng màu nền chế độ tối (để trống ô đó thì web dùng Màu nền trang). Ví dụ theme Halloween: chọn Luôn tối, rồi chọn màu cam cháy, tím sáng cho tiêu đề và lời chào mà không phải lo màu có đọc được ở chế độ sáng hay không. Lựa chọn khóa được lưu cùng từng theme, nên Halloween luôn tối còn theme thường vẫn để khách tự chọn.
- Tất cả các mục mới trên đều được lưu cùng **Bộ theme**, nên mỗi theme có thể có biểu tượng, phông, màu chữ và hiệu ứng icon rơi riêng.
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
- Dưới khung đếm iris ở trang Chào mừng có nút xanh lá **Mời thưởng trà**. Bấm vào thì hiện lời mời một món ngẫu nhiên (xem mục **Món mời thưởng trà** bên dưới). Chữ trên nút sửa trong `index.html`, khóa `tea` ở đối tượng `T`.

## Món mời thưởng trà (tab Món mời trà trong admin)
- Khi khách bấm nút **Mời thưởng trà**, web hiện một hộp nhỏ giữa màn hình có hình một món và câu "Cô chủ Cottage mời bạn một ... hôm nay". Món được bốc ngẫu nhiên trong danh sách của bạn. Mỗi lần khách ghé web (một phiên duyệt web) được bốc một món và giữ món đó cho tới khi họ đóng tab, lần ghé sau bốc món mới. Bấm nút "Cảm ơn cô chủ, cho tôi vào đọc bài" thì sang mục Bài viết. Bấm dấu ×, bấm ra ngoài hộp hoặc phím Esc thì chỉ đóng hộp.
- Danh sách trống thì nút **Mời thưởng trà** vẫn đưa khách thẳng sang mục Bài viết như trước.
- Thêm món: vào tab **Món mời trà**, bấm **＋ Thêm món từ ảnh**, chọn một hoặc nhiều ảnh cùng lúc (nên là PNG nền trong, web tự thu nhỏ về khoảng 600 px). Mỗi ảnh thành một dòng món, tên món điền sẵn theo tên file để bạn sửa lại. Điền tên tiếng Việt và tiếng Pháp (bỏ trống bên nào thì web dùng bên còn lại), rồi bấm **Lưu danh sách món**. Web cập nhật sau khoảng 1 phút.
- Danh sách thêm bao nhiêu món cũng được. Mỗi món có nút **Đổi ảnh** và **Xóa món**. Mỗi ảnh tải lên được lưu vào thư mục `media/` của repo.
- Vì tiếng Việt cần loại từ, hãy ghi tên món kèm loại từ cho tự nhiên (vd: "tách trà hoa cúc", "chiếc bánh madeleine"). Bản tiếng Pháp nên ghi kèm mạo từ (vd: "une tasse de thé"). Câu mời và chữ trên nút đổi được ngay trong tab, ghi `{item}` ở chỗ muốn hiện tên món. Bấm **Xem thử một lời mời** để xem câu ghép ra có tự nhiên không.

## Món đi cùng khách (nút "Gọi món khác")
- Sau khi khách đã nhận lời mời thưởng trà (đóng hộp lời mời bằng bất kỳ cách nào), hình món được mời ở lại bên mép trái, giữa chiều cao màn hình, và nhẹ nhàng nhấp nhô lên xuống trong suốt lúc khách đọc. Ngay dưới hình có dòng chữ gạch chân **Gọi món khác**. Bấm vào hình hoặc dòng chữ thì sang trang Gọi món.
- Món này là món đã bốc cho khách trong lần ghé đó, đổi qua lại giữa các trang hay đổi ngôn ngữ vẫn giữ nguyên, tới lần ghé sau mới bốc món mới. Khi khách đang ở trang Gọi món thì ô này tự ẩn. Món chưa có ảnh thì hiện hình tách trà thay thế.
- Hình lấy từ ảnh của món trong tab **Món mời trà** hoặc **Gọi món**, nên bạn không cần cài đặt thêm gì. Chữ "Gọi món khác" (tiếng Pháp: "Un autre plat") nằm trong `index.html`, ở hằng số `CMP`.

## Mục Gọi món / À la carte (tab Gọi món trong admin)
- Mục **Gọi món** trên thanh menu là một tờ thực đơn gồm 3 phần: **Khai vị**, **Món chính**, **Tráng miệng** (bản tiếng Pháp: Entrées, Plats, Desserts). Mỗi món hiện hình và tên theo ngôn ngữ khách chọn. Phần nào chưa có món thì tự ẩn.
- **Danh sách món dùng chung với "Mời thưởng trà".** Món nào có trong tab **Món mời trà** thì có trong trang Gọi món, và ngược lại. Thêm hay xóa món ở tab nào cũng được, món xuất hiện hoặc biến mất ở cả hai nơi (trang Chào mừng và trang Gọi món) sau khi bấm lưu và chờ khoảng 1 phút.
- **Phân loại**: mỗi món có ô chọn Khai vị / Món chính / Tráng miệng. Tab **Gọi món** chia sẵn 3 khu, mỗi khu có nút **＋ Thêm món từ ảnh** (chọn nhiều ảnh một lúc, món mới tự vào đúng phần) và **＋ Thêm món chưa có ảnh**. Ở tab **Món mời trà** có ô "Phân loại cho các món sắp thêm". Đổi ô phân loại của một món thì món tự chuyển sang phần mới.
- Món cũ chưa được phân loại sẽ tạm hiện ở **Món chính**, ô phân loại của nó ghi "Chưa phân loại". Bạn chọn lại cho đúng rồi bấm lưu.
- Tab Gọi món còn cho sửa **tiêu đề** và **lời dẫn** đầu trang thực đơn (VI/FR, bỏ trống thì dùng câu mặc định). Bấm **Lưu thực đơn** để lưu cả món lẫn chữ.
- **Ô cửa sổ vòm trưng bày**: mỗi món trên trang Gọi món nằm trong một ô cửa sổ vòm viền vàng, có kệ gỗ phía dưới và bảng tên món bên dưới ô. Rê chuột vào (hoặc bấm trên điện thoại) thì ô nhấc nhẹ lên và có vệt sáng lướt qua kính.
- **Câu chuyện hoặc fact của từng món**: khách bấm vào ô nào thì hiện một hộp vòm có hình món, phân loại, tên món và phần **Câu chuyện đằng sau món** (bấm ×, bấm ra ngoài hoặc phím Esc để đóng). Bạn viết nội dung này ở ô **Câu chuyện hoặc fact về món này** của từng món, trong tab **Gọi món** hoặc tab **Món mời trà** (bấm vào dòng chữ đó để mở rộng ô). Có hai ô tiếng Việt và tiếng Pháp (bỏ trống bên nào thì web dùng bên còn lại), cách 1 dòng trống để sang đoạn mới. Món chưa có câu chuyện thì hộp hiện một dòng báo cô chủ cottage đang viết thêm. Nhớ bấm **Lưu thực đơn** (hoặc **Lưu danh sách món**) sau khi viết.
- Dữ liệu lưu trong `data/site.json`: món nằm ở `treats.items` (thêm trường `cat` là `starter`, `main` hoặc `dessert`, và `storyVi`, `storyFr` cho câu chuyện), chữ trang thực đơn ở khóa `menu`.

## Hiệu ứng icon rơi ở nền (tab Giao diện trong admin)
- Mục **Hiệu ứng icon rơi ở nền** cho icon nhẹ nhàng rơi trên toàn web, ví dụ tuyết cho Giáng sinh. Đổi được: bật/tắt, loại icon (bông tuyết, hạt tuyết tròn, hoa iris nhỏ, hoặc hình của bạn: PNG nền trong, vd cánh mai, lá phong, bí ngô, dơi), số lượng, cỡ, tốc độ rơi, độ đậm, và lớp hiển thị (phía sau chữ như nền, hoặc phía trước phủ lên cả nội dung).
- Chỉnh xong bấm **Lưu thiết kế** rồi mở web để xem. Hiệu ứng được lưu cùng từng **Bộ theme**, nên theme Giáng sinh rơi tuyết, theme Halloween rơi bí ngô, theme thường không rơi gì.
- Máy khách bật chế độ giảm chuyển động thì hiệu ứng tự tắt, màn hình điện thoại tự giảm bớt số lượng. Hình của bạn được thu nhỏ về khoảng 256 px khi tải lên nên rất nhẹ.
- Đây là hiệu ứng riêng, không liên quan tới "Hình rơi quanh thiệp" trong tab Thư chào (cái đó chỉ rơi quanh tấm thiệp lúc khách vừa mở web).

## Mục Ngẫu nhiên: bộ 36 lá bài từ vựng (tab Ngẫu nhiên trong admin)
- Mục **Ngẫu nhiên** trên thanh menu hiện 36 lá bài úp, cùng một mặt sau. Khách bấm một lá thì lá đó lật ra (khách thấy từ tiếng Pháp hiện trên lá), rồi một lá bài lớn hiện giữa màn hình, lật ra mặt trước là một bức thư ghi: **từ tiếng Pháp**, **giống** (đực, cái, hoặc cả hai), **loại từ**, **nghĩa tiếng Việt**, **câu ví dụ tiếng Pháp** và **nghĩa của câu ví dụ**. Bấm dấu ×, ra ngoài lá bài hoặc phím Esc để đóng. Lá đã lật có chữ từ hiện trên lá, bấm lại để xem lại. Nút **Xáo lại bài** chia lại bài từ đầu.
- **Thêm từ**: vào tab **Ngẫu nhiên**, mục **Thêm từ mới**, điền từ, chọn giống, chọn loại từ, gõ nghĩa và câu ví dụ, rồi bấm **Thêm và lưu lên web** (web cập nhật sau khoảng 1 phút). Chỉ bắt buộc có từ tiếng Pháp, các ô còn lại bỏ trống thì lá bài không hiện phần đó. Từ nào cần sửa, bấm **Sửa** ở danh sách bên dưới. Danh sách có ô tìm kiếm và nút **Xóa**. Từ mới thêm nằm trên cùng danh sách.
- **Nhập nhiều từ một lúc**: mở mục "Dán danh sách từ", mỗi dòng một từ, các cột cách nhau bằng dấu `|` (hoặc dán thẳng từ Excel, Google Sheets). Thứ tự cột: `từ | giống | loại từ | nghĩa | câu ví dụ | nghĩa câu ví dụ`. Giống ghi `m`, `f`, `mf` hoặc để trống. Loại từ ghi tên tiếng Việt hoặc tiếng Pháp (danh từ/nom, động từ/verbe, tính từ/adjectif, trạng từ/adverbe, giới từ/préposition, liên từ/conjonction, đại từ/pronom, mạo từ/article, thán từ/interjection, cụm từ/locution, thành ngữ/expression). Ví dụ: `la maison | f | danh từ | ngôi nhà | Ma maison est petite. | Nhà của tôi nhỏ.` Các cột cuối có thể bỏ trống, dòng nào thiếu từ tiếng Pháp bị bỏ qua.
- **Cách chia bài**: có từ 36 từ trở lên thì mỗi lá là một từ khác nhau, và mỗi lần khách vào web (hoặc bấm Xáo lại bài) web bốc ngẫu nhiên 36 từ trong danh sách của bạn. Dưới 36 từ thì web vẫn đủ 36 lá nhưng một số từ lặp lại ở nhiều lá. Chưa có từ nào thì trang hiện lời nhắn khách quay lại sau.
- **Thiết kế lá bài** (cùng tab): bấm **Chọn hình** ở **Mặt sau** để tải thiết kế của bạn, cả 36 lá dùng chung mẫu này. Ảnh dọc tỉ lệ 5:8 (vd 750×1200 px) hiện trọn vẹn, tỉ lệ khác bị cắt vừa khung. Chưa tải thì dùng mẫu mặc định (nền màu header, họa tiết ô trám và hoa iris ở giữa). **Mặt trước** mặc định là một bức thư cũ có con tem hoa iris; nếu muốn thay bằng thiết kế riêng, tải ảnh ở mục mặt trước (cũng tỉ lệ 5:8), chữ từ vựng sẽ nằm đè lên ảnh, bạn chọn được màu chữ và bật **nền giấy mờ** sau chữ cho dễ đọc. Sửa xong bấm **Lưu bộ bài**.
- Chữ trên lá bài đổi theo VI/FR của web: nhãn giống, loại từ, chữ "Ví dụ" và lời dẫn đầu trang (sửa được trong admin). Nội dung nghĩa và câu ví dụ là phần bạn nhập nên giữ nguyên ở cả hai ngôn ngữ.
- Dữ liệu lưu trong `data/site.json`, khóa `cards`. Ảnh thiết kế lá bài lưu trong `media/`.

## Lá bài bí ẩn ở mục Bài viết
- Ở khu vực **Bài viết** (cả danh sách bài lẫn trang đọc từng bài), một lá bài tím có dấu hỏi chấm vàng lơ lửng ở lề phải màn hình, đung đưa nhẹ và lấp lánh. Rê chuột vào thì hiện dòng "Rút một lá bài" (hoặc "Tirez une carte" khi chọn FR), bấm vào sẽ chuyển sang mục **Ngẫu nhiên** để khách rút bài.
- Lá bài chỉ hiện ở mục Bài viết, không hiện ở Chào mừng, Ngẫu nhiên và Giới thiệu. Trên điện thoại lá bài nhỏ hơn và nằm góc dưới bên phải. Khách bật chế độ giảm chuyển động thì lá bài đứng yên.
- Muốn đổi dòng chữ hiện ra khi rê chuột, sửa `RN.vi.title` và `RN.fr.title` trong `index.html` (cũng là tiêu đề của mục Ngẫu nhiên).

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
