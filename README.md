# Bot Discord Hỗ Trợ Đa DB Pterodactyl

## Giới thiệu

Đây là một bot Discord được phát triển bằng TypeScript, được thiết kế để đọc và quản lý dữ liệu từ nhiều cơ sở dữ liệu MySQL của Pterodactyl. Bot cung cấp các tính năng hữu ích như quản lý điểm số, yêu cầu ngân hàng, hệ thống coupon, và xử lý thẻ nạp tiền một cách an toàn và hiệu quả.

Bot này giúp quản lý server Minecraft với tích hợp sâu vào các plugin phổ biến, cho phép người dùng và admin tương tác dễ dàng qua Discord.

## Plugin Hỗ Trợ

Bot tích hợp với các plugin Minecraft sau để cung cấp chức năng đầy đủ:

- **CMI (Chat Manager Interface)**: Quản lý người dùng, nickname, và dữ liệu người chơi.
- **PlayerPoints**: Hệ thống điểm số cho người chơi, hỗ trợ cộng/trừ điểm và bảng xếp hạng.
- **Vault**: Tích hợp với hệ thống kinh tế (nếu cần).
- **Pterodactyl Panel**: Kết nối trực tiếp với cơ sở dữ liệu MySQL của server Pterodactyl.

## Yêu cầu Hệ thống

- Node.js 18 hoặc phiên bản mới hơn
- npm
- Máy chủ MySQL (Pterodactyl database)
- Bot Discord với quyền cần thiết

## Cài đặt

1. Sao chép file cấu hình:
   ```bash
   cp .env.example .env
   ```
   Điền thông tin Discord và mật khẩu DB vào `.env`.

2. Cập nhật `db-profiles.json` với thông tin cơ sở dữ liệu của bạn.

3. Cài đặt dependencies:
   ```bash
   npm install
   ```

4. Đăng ký lệnh slash:
   ```bash
   npm run register
   ```

5. Chạy bot:
   ```bash
   npm run dev  # Chế độ phát triển
   npm run build:clean && npm run start  # Sản xuất
   ```

## Lệnh Người Dùng (User Commands)

Các lệnh dành cho người dùng thông thường:

- /pointslead [top:10] - Xem bảng xếp hạng điểm top 10 (hoặc số tùy chỉnh).
- /card type:`LoạiThẻ` amount:`SốTiền` code:`MãThẻ` serial:`Serial` username:`TênNgườiDùng` - Nạp thẻ (chỉ trong kênh ticket).
- /bank server:`Cụm` amount:`SốTiền` username:`TênNgườiDùng` - Tạo QR chuyển khoản (chỉ trong kênh ticket).
- /kkay help - Hiển thị danh sách lệnh cơ bản.

## Lệnh Admin

Các lệnh dành cho admin (yêu cầu quyền admin):

- /points info username:`TênNgườiDùng` - Xem thông tin điểm của người dùng.
- /points give username:`TênNgườiDùng` amount:`Xu` - Cộng điểm cho người dùng.
- /points take username:`TênNgườiDùng` amount:`Xu` - Trừ điểm của người dùng.
- /admin bank type:`LoạiNgânHàng` account_number:`SốTàiKhoản` - Cấu hình ngân hàng cho server.
- /admin bankstatus - Xem trạng thái ngân hàng hiện tại.
- /admin serveradd name:`TênCụm` - Thêm cụm server.
- /admin serverdel name:`TênCụm` - Xóa cụm server.
- /admin serverlist - Liệt kê các cụm server.
- /admin help - Hiển thị danh sách lệnh admin.
- /admin showplaytime username:`TênNgườiDùng` - Xem thời gian chơi của người dùng.
- /admin setplaytime username:`TênNgườiDùng` time:`ThờiGian` - Đặt thời gian chơi (vd: 3600, 2h, 01:30:00).
- /admin ban username:`TênNgườiDùng` time:`ThờiGian` reason:`LýDo` - Ban người dùng.
- /admin unban username:`TênNgườiDùng` - Unban người dùng.
- /admin mute username:`TênNgườiDùng` time:`ThờiGian` reason:`LýDo` - Mute người dùng.
- /admin unmute username:`TênNgườiDùng` - Unmute người dùng.
- /admin checkdup [page:1]` - Kiểm tra tài khoản trùng lặp.
- /admin remacc uuid:`UUID` - Xóa tài khoản theo UUID.
- /coupon start target:`MụcTiêu` percent:`PhầnTrăm` time_or_limit:`ThờiGianHoặcGiớiHạn` - Bắt đầu chương trình coupon.
- /coupon end target:`MụcTiêu` - Kết thúc chương trình coupon.
- /coupon status - Xem trạng thái coupon hiện tại.

## Bảo Mật và Lưu Ý

- Không commit mật khẩu hoặc thông tin nhạy cảm vào Git.
- Sử dụng SSH tunnel nếu DB không mở port công khai.
- Bot sử dụng mã hóa cho dữ liệu nhạy cảm và có hệ thống queue để ngăn chặn lỗi.
- Kiểm tra quyền bot Discord: `bot`, `applications.commands`, và các quyền cần thiết cho kênh.

## Khắc Phục Sự Cố

- Nếu lệnh không xuất hiện: Kiểm tra `GUILD_ID`, `DISCORD_TOKEN`, và quyền invite bot.
- Lỗi DB: Kiểm tra host/port, user/password, và firewall.
- Queue đầy: Chờ hoặc liên hệ admin.

## Đóng Góp

Nếu bạn muốn đóng góp, hãy tạo issue hoặc pull request trên GitHub.

## Giấy Phép

Dự án này sử dụng giấy phép MIT.

## Contact
Disscord: _nguyenminhhieu
