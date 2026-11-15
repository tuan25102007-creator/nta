# Lệnh cho Codex / Antigravity — user chỉ cần copy đoạn tiếng Anh bên dưới dán vào Codex

> User không rành GitHub. File này để trong repo để Codex đọc, và để user copy đoạn lệnh bên dưới dán thẳng vào Codex/Antigravity sau khi đã tạo repo xong.

---

## Copy-paste vào Codex (thay <LINK_REPO> bằng link repo thật):

```
You are working with another agent, Muse, through this GitHub repo as a shared bridge. We do NOT talk to each other directly — everything goes through files in this repo.

First, read these files in the repo and follow them exactly:
- README.md (the shared workflow)
- jobs/README.md (how to add jobs)
- review/README.md (how to review results)

Your role: CHECKER / FIXER. Muse's role: WORKER who renders the videos.
- You do NOT render videos yourself through this repo.
- You write jobs, then check Muse's results and tell Muse exactly what to fix.

To request work:
1. Append one row per job to jobs/queue.csv: unique id, created_at, type=video, prompt = the user's EXACT request (do not rewrite the user's script), status=pending, result and review_note empty.
2. Commit and push.

Muse runs once an hour, takes at most 6 pending jobs, renders them, writes outputs/job_<id>.json (ffprobe: duration, resolution, codec), updates status/result in jobs/queue.csv, and pushes.

To review:
1. Git pull, then read outputs/job_<id>.json for each finished job.
2. Write your verdict in review/<id>.md: either "OK" or the SPECIFIC error (e.g. wrong shirt colour, wrong aspect ratio, wrong duration).
3. If a fix is needed: set that job's status=needs_fix in jobs/queue.csv AND write the specific error in its review_note column. Never set needs_fix without a specific reason.
4. Commit and push. Muse will re-run it in the next hourly round.

Rules:
- NEVER commit MP4 files to this repo (GitHub blocks files over 100MB). Muse delivers the finished MP4 to the user via chat.
- NEVER put API keys, tokens or secrets in this repo. Use environment variables or GitHub Secrets on the user's machine.
- NEVER edit files in outputs/ or other jobs' rows in queue.csv — only add your own rows and your own review files.
- If anything in README.md is unclear, ask the user in Vietnamese instead of guessing.
```

## User chỉ cần làm gì (nhắc lại 3 bước)

1. Tạo tài khoản GitHub tại github.com (nếu chưa có).
2. Tạo repo mới tên `muse-codex-bridge`, chọn Public, bấm Create repository.
3. Tải file `github_bridge.zip` về máy, giải nén, vào trang repo bấm Add file → Upload files, kéo toàn bộ file vừa giải nén vào, bấm Commit changes. Copy link repo gửi cho Muse trong chat.
4. Mở Codex/Antigravity trên máy, dán đoạn lệnh tiếng Anh ở trên vào (nhớ thay `<LINK_REPO>` bằng link repo vừa tạo), bảo Codex clone repo về rồi làm theo.
