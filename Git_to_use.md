### Công việc
> git checkout master
> git fetch
> git merge origin/master
> git checkout -b feedback_form
> git add feedback.html
> git commit -m "Add customer feedback form"
> git fetch
> git push-u origin feedback_form
 
### Coworker
> git checkout master
> git fetch
> git merge origin/master
> git checkout -b feedback_form origin/feedback_form
> git log
> git show 8284abdq9
> git commit -am "Add tour selector to feedback form"
> git fetch
> git push
 
### My work
> git fetch
> git log -p feedback_form..origin/feedback_form
> git merge origin/feedback_form
> git checkout master
> git fetch
> git merge origin/master
> git merge feedback_form
> git push

### Thao tác khi source thay đổi
> # đưa các file bị thay đổi vào staging index

> git add .
 
> # lưu vào repository kèm theo thông tin ghi chú

> git commit -m "Initial commit"
 
> # add và commit cùng lúc

> git commit -am "Initial commit"
 
> # thay đổi nội dung ghi chú hoặc ghi đè lên commit
> # gần nhất

> git commit --ammend "Ammend the commit"
