# tmux

1. tmux的使用，安装

2. 基本使用方法，创建多窗口等；

   ```
   ctl + b,   "        横向分割窗口
   ctl + b,   %        竖向分割窗口 
   ctl + b,   方向      切换窗口
   exit                 关闭窗口
   ```

   ```
   Ctrl+b,    c        创建一个新的窗口页
   Ctrl+b,    p/n      移动窗口页
   Ctrl+b,    d        脱离一个会话框
   ```

   ```
   tmux attach-session/attach   重新进入之前的会话框
   tmux list-sessions           列出会话框
   ```



- `C-b ?` 列出所有快捷键, 按q或Esc返回
- `C-b d` detach当前会话,可暂时返回Shell界面，输入tmux attach能够重新进入之前会话
- `C-b s` 选择并切换会话；在同时开启了多个会话时使用
- `C-b c` 创建一个新窗口
- `C-b &` 关闭当前窗口
- `C-b w` 列出所有的窗口选择
- `C-b p` 切换到上一个窗口
- `C-b n` 切换到下一个窗口
- `C-b 窗口号` 使用窗口号切换窗口(例如窗口号为1的, 则`C-b 1`)
- `C-b ,` 重命名当前窗口，便于识别各个窗口
- `C-b %` 横向分Terminal
- `C-b "` 纵向分Terminal
- `C-b 方向键` 则会在自由选择各面板
- `C-b x` 关闭当前pane
- `C-b q` 显示面板编号