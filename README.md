# Cầu nối GitHub: Codex / Antigravity <-> Muse

Repo này là "cầu nối" để hai agent làm việc chung. Hai bên KHÔNG nói chuyện
trực tiếp với nhau — mọi thứ đi qua file trong repo này.

## Luồng làm việc

1. **Codex/Antigravity (chạy trên máy user)** thêm việc vào `jobs/queue.csv`
   (status=pending), rồi commit + push.
2. **Muse** mỗi giờ `git pull`, đọc queue, chạy tối đa 6 việc video đang chờ,
   ghi MP4 + file kiểm chứng `outputs/job_<id>.json` (ffprobe: thời lượng,
   độ phân giải, codec), cập nhật status/result trong queue.csv, commit + push.
3. **Codex** kiểm tra kết quả, ghi nhận xét vào `review/<id>.md`. Nếu cần sửa:
   đặt status=`needs_fix` trong queue.csv (kèm ghi chú ở cột review_note);
   Muse sẽ chạy lại việc đó ở lượt sau.
4. File MP4 hoàn chỉnh Muse vẫn gửi kèm về chat chính cho user tải về
   (GitHub không hợp để chứa file video lớn; file >100MB bị chặn).

## Quy ước cột trong jobs/queue.csv

id,created_at,type,prompt,status,result,review_note

- type: video (clip AI 10 giây)
- status: pending | running | done | failed | needs_fix
- result: đường dẫn file output hoặc lý do lỗi ngắn gọn
- review_note: ghi chú của Codex (chỉ Codex ghi)

## Lưu ý

- Codex/Antigravity có quyền truy cập máy user; Muse chỉ thấy đúng những gì
  trong repo này và chat. Không chia sẻ key/token trong repo — dùng GitHub
  Secrets hoặc biến môi trường trên máy user.
