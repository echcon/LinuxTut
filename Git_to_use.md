### Thiết lập thông số lần đầu làm việc
<code> git config --global user.name "chithong"</code
git config --global user.email "chithongn@gemail.com"
 
### Công việc
<code> git checkout master</code><br/>
<code> git fetch</code><br/>
<code> git merge origin/master</code><br/>
<code> git checkout -b feedback_form</code><br/>
<code> git add feedback.html</code><br/>
<code> git commit -m "Add customer feedback form"</code><br/>
<code> git fetch</code><br/>
<code> git push-u origin feedback_form</code><br/>
 
### Coworker
<code> git checkout master</code><br/>
<code> git fetch</code><br/>
<code> git merge origin/master</code><br/>
<code> git checkout -b feedback_form origin/feedback_form</code><br/>
<code> git log</code><br/>
<code> git show 8284abdq9</code><br/>
<code> git commit -am "Add tour selector to feedback form"</code><br/>
<code> git fetch</code><br/>
<code> git push</code><br/>
 
### Kiểm tra branch
<code> git fetch</code><br/>
<code> git log -p feedback_form..origin/feedback_form</code><br/>
<code> git merge origin/feedback_form</code><br/>
<code> git checkout master</code><br/>
<code> git fetch</code><br/>
<code> git merge origin/master</code><br/>
<code> git merge feedback_form</code><br/>
<code> git push</code><br/>

### Thao tác khi source thay đổi
> ***đưa các file bị thay đổi vào staging index***
<code> git add .</code><br/>
<code> ##### lưu vào repository kèm theo thông tin ghi chú</code><br/>
<code> git commit -m "Initial commit"</code><br/>
<code>  ***add và commit cùng lúc*** </code><br/>
<code> git commit -am "Initial commit"</code><br/>
 
***thay đổi nội dung ghi chú hoặc ghi đè lên commit gần nhất***

<code> git commit --ammend "Ammend the commit"</code>

### Branch
#### liệt kê danh sách các branch
<code> git branch</code>
 
#### xem con trỏ HEAD đang ở branch nào
<code> cat .git/HEAD</code>
 
#### xem có bao nhiêu branch trong head
<code> cat .git/refs/heads/</code>
 
#### head đang trỏ đến commit nào
<code> cat .git/refs/heads/master</code>
 
### tạo lập branch mới
<code> git branch new_branch</code>
#### vừa tạo vừa chuyển qua new_branch cùng lúc
<code> git checkout -b new_branch</code>

### Chuyển bbranch nhưng bị vướng uncommit
#### cách 1: undo những thay đổi
<code> git checkout -- index.html</code>
 
#### cách 2: commit các thay đổi còn tồn tại
<code> git commit -am "Commit changes"</code> 

#### cách 3: lưu tạm vào stash (nơi lưu trữ bí mật)
<code> git stash save "changed mission page title"</code> 

### Thay đổi dấu nhắc lệnh của command line để quan sát branch hiện hành
#### mở file .bashrc, sau đó thêm dòng lênh
<code> export PS1='\W$(__git_ps1 "(%s)") > '</code>
 
#### nạp lại .bashrc để thấy kết quả
<code> source .bashrc</code>
 
#### kết quả thu được
<code> testing(new_branch) ></code>
