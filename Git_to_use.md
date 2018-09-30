### Công việc
<code>*git checkout master*</code>
<code>*git fetch*</code>
<code>* git merge origin/master*</code>
<code> git checkout -b feedback_form</code>
<code> git add feedback.html</code>
<code> git commit -m "Add customer feedback form"</code>
<code> git fetch</code>
<code> git push-u origin feedback_form</code>
 
### Coworker
<code> git checkout master</code>
<code> git fetch</code>
<code> git merge origin/master</code>
<code> git checkout -b feedback_form origin/feedback_form</code>
<code> git log</code>
<code> git show 8284abdq9</code>
<code> git commit -am "Add tour selector to feedback form"</code>
<code> git fetch</code>
<code> git push</code>
 
### Kiểm tra branch
<code> git fetch</code>
<code> git log -p feedback_form..origin/feedback_form</code>
<code> git merge origin/feedback_form</code>
<code> git checkout master</code>
<code> git fetch</code>
<code> git merge origin/master</code>
<code> git merge feedback_form</code>
<code> git push</code>

### Thao tác khi source thay đổi
> ***đưa các file bị thay đổi vào staging index***
<code> git add .</code>
<code> ##### lưu vào repository kèm theo thông tin ghi chú</code>
<code> git commit -m "Initial commit"</code>
<code>  ***add và commit cùng lúc*** </code>
<code> git commit -am "Initial commit"</code>
 
***thay đổi nội dung ghi chú hoặc ghi đè lên commit gần nhất***

<code> git commit --ammend "Ammend the commit"</code>
