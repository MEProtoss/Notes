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

## linux配置开机免密码登录

step1:

```shell
~ sudo nvim /etc/systemd/system/getty.target.wants/getty@tty1.service

  ExecStart=-/sbin/agetty --autologin time --noclear %I $TERM

```

step2:

```shell
~ sudo visudo
[用户名] ALL=(ALL:ALL) NOPASSWD: ALL

用户提权
yay -S polkit


```

## 可视化网络管理工具

nm-connection-editor

## 一些好玩的小工具

[终端玩具](https://arch.icekylin.online/guide/advanced/beauty-3.html#_2-zsh-%E7%BE%8E%E5%8C%96)

## 包管理工具pacman和yay

```bash
sudo pacman -S package_name # 安装软件包
pacman -Ss # 在同步数据库中搜索包，包括包的名称和描述
sudo pacman -Syu # 升级系统。 -y:标记刷新、-yy：标记强制刷新、-u：标记升级动作（一般使用 -Syu 即可）
sudo pacman -Rns package_name # 删除软件包，及其所有没有被其他已安装软件包使用的依赖包
sudo pacman -R package_name # 删除软件包，保留其全部已经安装的依赖关系
pacman -Qi package_name # 检查已安装包的相关信息。-Q：查询本地软件包数据库
pacman -Qdt # 找出孤立包。-d：标记依赖包、-t：标记不需要的包、-dt：合并标记孤立包
sudo pacman -Rns $(pacman -Qtdq) # 删除孤立包
sudo pacman -Fy # 更新命令查询文件列表数据库
pacman -F some_command # 当不知道某个命令属于哪个包时，用来在远程软件包中查询某个命令属于哪个包（即使没有安装）
pactree package_name # 查看一个包的依赖树

```

- yay 的用法和 Pacman 是基本一样的。有额外几条常用命令：

```bash
yay # 等同于 yay -Syu
yay package_name # 等同于 yay -Ss package_name && yay -S package_name
yay -Ps # 打印系统统计信息
yay -Yc # 清理不需要的依赖

```

- 可视化包管理工具

```bash
yay -S octopi
```
