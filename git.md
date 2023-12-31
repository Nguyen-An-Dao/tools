# Các lệnh Git
## Cấu hình và khởi tạo Repo
```git config --global user.name newname```
đổi tên người dùng

```git config --global user.email newmail@domain.com```
đổi email

```git init```
khởi tạo một Local Repository mới

```git init --bare```
khởi tạo một Remote Repository mới ở Git Server

## Làm việc với Local Repo
```git status```
trạng thái của Repo

```git status -s```
trạng thái của Repo ngắn gọn

```git clone path```
sao chép một Repository có địa chỉ là path

```git add```
cập nhật vào staged

```git add filename```
thêm file vào staged

```git add *.c```
file có phần mở rộng .c

```git add -A```
thêm mọi thứ có sự thay đổi (file mới, xóa file, nội dung 
thay đổi ...)

```git add .```
thêm mọi thứ trừ loại xóa file

```git add -```
thêm mọi thứ trừ file mới

```git commit -m "Thông báo ..."```
commit mới

```git commit --amend -m "Thông báo ..."```
commit + cập nhật vào commit cuối

```git log```
lịch sử commit

```git log -4```
lịch sử 4 commit

```git log -4 -p```
lịch sử 4 commit + chi tiết thay đổi

```git log --pretty=oneline```
Hiện thị trực quan trên 1 dòng

```git log --oneline```
Hiện thị trên 1 dòng

```git diff```
Xem sự khác biệt giữa thư mục làm việc và staged

```git diff --staged```
Xem sự khác biệt giữa staged và commit cuối

```git rm filename```
xóa file

```git reset HEAD filename```
hủy thay đổi của file

```git checkout -- filename```
khôi phục thay đổi của file

```git checkout [hash] filename```
khôi phục từ commit có mã hash

```git checkout [hash] .```
khôi phục các file từ commit có mã hash

```git clean -d -fx .```
Xóa các file không được theo dõi, có ích khi muốn xóa bỏ nhanh các file không được theo dõi
## Làm việc với Remote Repo
```git remote```
xem các Remote

```git remote -v```
xem các Remote

```git remote add name_remote addr_remote```
thêm một Remote vào Local

```git fetch name_remote```
cập nhật Local Repo từ Remote Repo

```git pull name_remote name_branch```
cập nhật Local Repo từ Remote Repo

```git push name_remote name_branch```
cập nhật Local Repo từ Remote Repo

```git remote show name_remote```
xem thông tin về Remote

```git remote rename abc xyz```
đổi tên Remote

## Làm việc với Tag
```git tag```
xem danh sách tag

```git tag -a tagname -m "Ghi chú"```
tạo tag cho commit hiện tại

```git tag -a tagname -m "Ghi chú" hash```
tạo tag cho commit cũ

```git show tagname```
thông tin về commit có tagname

```git push origin tagname```
cập nhận lên remote tất cả tagname

```git push origin --tags```
cập nhận lên remote tất cả tag

```git checkout tagname```
về phiên bản commit có tagname

```git checkout -b newbranchname tagname```
tạo nhánh mới từ phiên bản tagname

```git push --delete origin tagname```
xóa tag ở remote

```git tag -d tagname```
xóa tag ở local
## Làm việc với nhánh
```git branch```
liệt kê các nhánh

```git branch -v```
liệt kê các nhánh + commit cuối

```git branch --merged```
các nhánh gộp vào nhánh này

```git branch --no-merged```
các nhánh không gộp vào nhánh này

```git branch branchname```
tạo nhánh mới

```git checkout -b branchname```
tạo nhánh mới, khi đang đứng ở một snapshot cũ

```git checkout branchname```
chuyển nhánh

```git merge branchname```
gộp nhánh với nhánh hiện tại

```git base branchname```
gộp nhánh với nhánh hiện tại

```git mergetool```
công cụ trực quan xử lý xung đột merge

```git branch -d branchname```
xóa nhánh
## Xóa toàn bộ lịch sử Commit
Xóa lịch sử toàn bộ commit trên nhánh :
master
```git checkout master   ```                              # chuyển về nhánh master

```git checkout --orphan temp_branch ```                  # tạo nhánh temp_branch không chứa lịch sử commit

```git add -A ```                                     # thêm các file vào nhánh

```git commit -am "Init```"                               # commit đầu tiên

```git branch -D master```                                # xóa nhánh master

```git branch -m master```                                # đổi tên nhánh hiện tại (temp_branch) thành master

```git push -f origin master```                           # push thay đổi lên Remote

## Một số trường hợp dùng Git

Phục hồi các file bị sửa đổi từ một commit, so với commit khác
```git checkout IDcommitB --  $(git diff --name-only IDcommitA IDcommitB)```