# Changelog - Antigravity Brain OS

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
