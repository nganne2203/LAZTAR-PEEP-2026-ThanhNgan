
+++
title = "Day 01 - 15/09/2026 (On-site)"
weight = 1
+++

# Báo cáo ngày 01

## 1. Mục tiêu học tập hôm nay

Hôm nay em bắt đầu làm quen với Git và GitHub, tập trung vào các thao tác cơ bản để quản lý mã nguồn và làm việc nhóm. Em muốn nắm rõ các khái niệm căn bản như khởi tạo repo, commit, push, pull, merge, stash và cách xử lý conflict.

## 2. Những gì em đã làm

- Khởi tạo repository Git bằng lệnh `git init`.
- Clone repository từ GitHub về máy bằng `git clone`.
- Thực hành tạo file, thêm thay đổi vào staging area bằng `git add`.
- Tạo commit mới với `git commit -m "..."`.
- Đẩy code lên GitHub bằng `git push`.
- Kiểm tra trạng thái repo bằng `git status`.
- Thêm remote cho repo bằng `git remote add origin ...`.
- Thực hành `git pull`, `git merge`, `git stash`, `git stash list`.
- Tìm hiểu và xử lý một số tình huống conflict khi merge nhánh.

## 3. Kiến thức đã học

- Git là công cụ quản lý phiên bản rất quan trọng trong lập trình.
- `git init` dùng để khởi tạo repo mới.
- `git add` cho phép đưa thay đổi vào vùng index trước khi commit.
- `git commit` lưu lại phiên bản hiện tại của dự án.
- `git push` đẩy thay đổi lên remote repository.
- `git pull` đồng bộ code mới nhất từ remote về local.
- `git merge` dùng để gộp nhánh vào nhánh chính.
- `git stash` hữu ích khi muốn tạm thời lưu công việc đang làm mà không commit.
- Khi merge có conflict, cần giải quyết thủ công rồi tiếp tục commit hoặc merge.

## 4. Cách xử lý Git conflict

Conflict xảy ra khi Git không thể tự quyết định phải giữ thay đổi nào, thường do hai nhánh cùng chỉnh sửa một đoạn mã hoặc một tệp. Em thực hiện theo quy trình sau:

1. Kiểm tra các tệp đang xung đột bằng `git status`.
2. Mở từng tệp, đọc các marker `<<<<<<<`, `=======` và `>>>>>>>` để phân biệt thay đổi ở nhánh hiện tại với thay đổi được đưa vào.
3. Chỉnh sửa để chọn một thay đổi hoặc kết hợp cả hai; sau đó xóa toàn bộ marker conflict.
4. Kiểm tra lại code, rồi đánh dấu tệp đã xử lý bằng `git add <ten-file>`.
5. Hoàn tất thao tác đang thực hiện:
   - Với merge: `git commit` hoặc `git merge --continue`.
   - Với rebase: `git rebase --continue`.
   - Với cherry-pick: `git cherry-pick --continue`.

Nếu chưa muốn tiếp tục, có thể quay lại trạng thái trước đó bằng `git merge --abort`, `git rebase --abort` hoặc `git cherry-pick --abort` tương ứng. Trước khi hoàn tất, cần chạy kiểm thử hoặc kiểm tra lại tệp đã sửa để tránh giữ nhầm thay đổi.

## 5. Những khó khăn gặp phải

- Ban đầu em còn nhầm lẫn giữa `git add`, `git commit` và `git push`.
- Khi merge hoặc cherry-pick có conflict, em cần đọc kỹ lỗi và xử lý từng phần thay vì commit vội.
- Cần luyện tập nhiều hơn để nhớ rõ thứ tự thao tác và ý nghĩa từng lệnh.

## 6. Kết luận

Ngày hôm nay em đã có một buổi học thực hành Git cơ bản rất bổ ích. Em đã nắm được các lệnh quan trọng và cách làm việc với repository. Việc thực hành nhiều lần sẽ giúp em thành thạo hơn và tự tin hơn trong các dự án sau này.

## 7. Ảnh minh họa trong quá trình học

![Git init](/images/reports/day-01/git-init.png)

![Git clone](/images/reports/day-01/git-clone.png)

![Git commit](/images/reports/day-01/git-commit.png)

![Git merge](/images/reports/day-01/git-merge.png)

![Git pull](/images/reports/day-01/git-pull.png)

![Git stash](/images/reports/day-01/git-stash.png)

![Git status](/images/reports/day-01/git-status.png)

![Git remote](/images/reports/day-01/git-remote.png)

## 8. Đánh giá cá nhân

Em thấy mình cần tiếp tục luyện tập và ghi nhớ các lệnh Git theo từng mục đích sử dụng. Đây là nền tảng rất quan trọng cho các bài học và dự án sau này, vì vậy em sẽ dành thời gian ôn tập thêm mỗi ngày.
