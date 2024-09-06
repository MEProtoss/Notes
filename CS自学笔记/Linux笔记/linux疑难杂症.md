# linux疑难杂症

## mount: unknown filesystem type ‘ntfs’

病因：使用的U盘文件为ntfs类型

- 安装ntfs-3g

## 安装微信

```bash
    git clone https://aur.archlinux.org/wechat-universal-bwrap.git
    cd wechat-universal-bwrap
    makepkg -si
```

## 如何将损坏的archlinux 恢复到之前的工作状态 尤其是无法正常进入系统的时候

- 单用户模式进入系统

  - grub 菜单的时候输入e
  
    ![img](/home/time/文档/Notes/CS自学笔记/Linux笔记/linux疑难杂症.assets/edit-grub-1.jpg)

- 找到以linux开头的行 在末尾添加 `init=/bin/bash` ，然后按F10或c-x进入单系统模式

![img](/home/time/文档/Notes/CS自学笔记/Linux笔记/linux疑难杂症.assets/edit-grub-1-1.jpg)

- 以读/写模式挂载根文件系统

  ```bash
  mount -n -o remount,rw /
  ```

- 去解决问题（例如查看日志）

```bash
tail -n 200 /var/log/pacman.log | less
# tail 命令将仅显示最后 10 条条目。因此，请将 200 替换为您自己的号码，以查看 pacman.log 文件。我将 "tail" 命令的输出通过管道传输到 "less" 命令以逐页显示结果。
```

## 一些好玩的小工具

[终端玩具](https://arch.icekylin.online/guide/advanced/beauty-3.html#_2-zsh-%E7%BE%8E%E5%8C%96)
