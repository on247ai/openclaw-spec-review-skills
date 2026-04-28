# Review Loop

## Mô hình review nhiều vòng
### Vòng 1
Tìm lỗi lớn về hướng đi, thiếu phạm vi, sai requirement.

### Vòng 2
Tìm thiếu edge case, inconsistency, test gap, rollout gap.

### Vòng 3
Chốt artifact đã đủ để approve hay chưa.

## Khi nào cần 3 reviewer
- RFC kiến trúc
- feature rủi ro cao
- security / data / migration / production workflow
- feature nhiều module

## Cách tổng hợp
- gom finding theo severity: blocker / major / minor
- chỉ đóng review khi mọi blocker được xử lý hoặc bác bỏ có lý do
