# Create multi account in 1 computer with git
[Link](https://truthseekers.io/multiple-github-accounts-on-one-computer/)

## Create SSH key
- Open cmd `cd C:\Users\pc\.ssh`
- Run `ssh-keygen -t rsa` 2 times (1 for personal **lai**, 1 for company **a**)
- Giờ sẽ có 4 file: **a,a.pub, lai,lai.pub**
- Mở github > Settings > SSH and GPG keys > New SSH Key.
- Copy nội dung trong file \*.pup vào Key, title đặt tên là tên máy tính.

## Add SSH Key to SSH-Agent
1. Start Menu
2. Search “Manage optional features”
3. Make sure “Open SSH Client” is in the list. If not, figure out how to add it.
4. Open “Services” from start menu
5. Scroll down to “OpenSSH Authentication Agent” and right-click “properties”.
6. Change startup type from “disabled” to “Automatic (Delayed Start)” so the SSH-Agent is turned on automatically after booting.
7. Restart computer??? These steps didn’t work until I restarted.

## Create SSH Config file *.ssh/config*
```
# Default Account (TruthSeekers for me.)
Host lai
   HostName github.com
   User git
   IdentityFile ~/.ssh/lai

# Other account (XYZ co)
Host company
   HostName github.com
   User git
   IdentityFile ~/.ssh/a
```

## Clone dự án xuống
- Tạo thư mục
- `git init`
- `git remote add origin git@lai:danglaiacc/tst1`
- `git config user.name "lai personal"`
- `git config user.email "danglaiacc@gmail.com"`
- Chú ý khi up code lên nhớ checkout đúng branch của git là được
