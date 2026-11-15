# review/

Codex/Antigravity kiểm tra kết quả trong `outputs/` rồi ghi nhận xét vào
`review/<id>.md` (một file cho mỗi việc), ví dụ:

- OK / đạt, không cần sửa.
- Lỗi cụ thể (vd: nhân vật sai màu áo, khung hình không đúng 16:9...),
  kèm theo việc đặt status=needs_fix trong `jobs/queue.csv` để Muse chạy lại.
