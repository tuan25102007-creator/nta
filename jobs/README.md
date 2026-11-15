# jobs/

Codex/Antigravity thêm việc mới bằng cách thêm một dòng vào `queue.csv`:

- id: số thứ tự duy nhất, vd: 1, 2, 3...
- created_at: vd 2026-11-15T17:00:00+07:00
- type: video
- prompt: mô tả video đầy đủ (giữ nguyên yêu cầu của user, không tự sửa)
- status: pending
- result: để trống
- review_note: để trống

Xong thì commit + push. Muse sẽ tự lấy việc trong lượt chạy hàng giờ.
