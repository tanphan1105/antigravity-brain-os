# Changelog - Antigravity Brain OS

## [4.4.0] Stability-Layer - 2026-04-26

### 🛡️ Nâng Cấp Lớp Ổn Định (Stability Layer Upgrades)
- **Graceful Degradation (Tường lửa Ý định):** Agent không còn "sập cứng" khi người dùng nhập sai lệnh. Giờ đây, nếu lệnh bị từ chối, Agent sẽ xuất `suggested_intent_templates` để hướng dẫn người dùng nhập đúng cú pháp.
- **Narrowing Stage (Cứu Hộ Selector):** Thêm một vòng lặp thu hẹp phạm vi. Nếu tìm thấy nhiều selector trùng nhau, Agent sẽ tự động dùng `parent_tag` hoặc `sibling_context` để cố gắng lọc ra thẻ độc nhất, thay vì bỏ cuộc ngay lập tức.
- **Post-Rollback Validation Loop:** Sau khi xảy ra sự cố và tiến hành Rollback, Agent bắt buộc phải chạy 1 vòng lặp kiểm tra để xác nhận DOM thực sự nguyên vẹn và không bị nhiễm mã rác `wpautop` do side-effects.
- **Phân Cấp Miễn Dịch (Suspect vs Leak):** Hệ thống miễn dịch giờ chia làm 2 cấp: `PATTERN_SUSPECT` (khả nghi, yêu cầu người duyệt lại) và `PATTERN_LEAK` (lặp lại mù quáng, khóa cứng hệ thống).
- **System Drift Monitor:** Bổ sung theo dõi độ lệch hệ thống. Nếu Agent liên tục sập vì sai số lượng Node (do các plugin tự động sinh ra), hệ thống sẽ báo động để con người điều chỉnh `noise_margin`.

## [4.3.0] Mnemosyne-Evolution - 2026-04-26

### 🚀 Nâng Cấp Kiến Trúc (Architecture Upgrades)
- **Halt Protocol Khép Kín:** Định nghĩa chính xác 4 trạng thái `HALT` (INTENT_REJECTED, VERIFICATION_FAILED, EMERGENCY_ROLLBACK_FAILED, PATTERN_LEAK). Bắt buộc đóng băng DOM, ghi log, và chờ lệnh `RESET_SAFE` từ con người.
- **Audit Trail (Kiểm Toán Độc Lập):** Bổ sung hệ thống ghi Log siêu nhẹ (Dưới 1KB, lưu tối đa 5 snapshots). Lưu trữ toàn bộ dấu vết (DTV snapshot, error type, outcome) để phục vụ gỡ lỗi sau sự cố.
- **Bằng Chứng Thép (Selector Evidence):** Loại bỏ hoàn toàn điểm số tự tin (`0.85`) mơ hồ của AI. Ép buộc Agent phải dùng giá trị Boolean (`exists_in_dom`, `unique_match`) để tự chấm điểm trước khi thực thi.
- **Context Hash Bất Biến:** Định nghĩa thuật toán băm bối cảnh siêu chặt chẽ `URL + Selector + Parent Tag + Sibling Checksum (5 siblings) + Intent` để triệt tiêu bệnh "ảo giác hệ thống".

### 🔧 Sửa Lỗi Nghiêm Trọng (Critical Fixes)
- **Vá Xung Đột Jidoka (C1):** Làm rõ khái niệm "Thực thi 1 lần duy nhất". Khẳng định **Atomic Rollback** là hành động cứu hộ khẩn cấp, được miễn trừ khỏi giới hạn số lần chạy. Cấm thử lại Rollback lần 2.
- **Chặn Mù Mờ Bộ Nhớ (M2/M3):** Định nghĩa rõ Thang Đo Mức Độ Nghiêm Trọng (Severity Scale 1-4) cho Lỗi, và tiêu chuẩn Vàng (Không Rollback + Pass Static Test) để được lưu vào Immutable Memory.
- **Khóa Trình Độ (Autonomy Gate):** Hệ thống sẽ tự kiểm tra xem Agent đã tích lũy đủ 10 mẫu thành công và 5 mẫu thất bại chưa. Nếu chưa đủ, tự động hạ cấp xuống Level 3.5 (Cần người giám sát).

### 🗑️ Loại Bỏ (Removed)
- Xóa bỏ cài đặt `max_retry_limit: 1` gây nhầm lẫn trong quá trình thực thi, siết chặt kỷ luật "One-Shot Execution".
