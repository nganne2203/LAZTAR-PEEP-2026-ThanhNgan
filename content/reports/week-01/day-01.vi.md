+++
title = "Ngày 01 - Báo cáo Git"
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

## 4. Những khó khăn gặp phải
- Ban đầu em còn nhầm lẫn giữa `git add`, `git commit` và `git push`.
- Khi merge hoặc cherry-pick có conflict, em cần đọc kỹ lỗi và xử lý từng phần thay vì commit vội.
- Cần luyện tập nhiều hơn để nhớ rõ thứ tự thao tác và ý nghĩa từng lệnh.

## 5. Kết luận
Ngày hôm nay em đã có một buổi học thực hành Git cơ bản rất bổ ích. Em đã nắm được các lệnh quan trọng và cách làm việc với repository. Việc thực hành nhiều lần sẽ giúp em thành thạo hơn và tự tin hơn trong các dự án sau này.

## 6. Ảnh minh họa trong quá trình học

![Git init](/images/reports/day-01/git-init.png)

![Git clone](/images/reports/day-01/git-clone.png)

![Git commit](/images/reports/day-01/git-commit.png)

![Git merge](/images/reports/day-01/git-merge.png)

![Git pull](/images/reports/day-01/git-pull.png)

![Git stash](/images/reports/day-01/git-stash.png)

![Git status](/images/reports/day-01/git-status.png)

![Git remote](/images/reports/day-01/git-remote.png)

## 7. Đánh giá cá nhân
Em thấy mình cần tiếp tục luyện tập và ghi nhớ các lệnh Git theo từng mục đích sử dụng. Đây là nền tảng rất quan trọng cho các bài học và dự án sau này, vì vậy em sẽ dành thời gian ôn tập thêm mỗi ngày.
