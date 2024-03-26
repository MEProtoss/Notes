# wsl下安装ubuntu 以及配置

1. Microsoft store中安装Ubuntu
2. 开启Windows的wsl系统功能
3. 升级wsl内核
   https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi
4. 启动创建账户

## 准备工作

查看当前环境安装的wsl
wsl --list
注销（卸载）当前安装的Linux的Windows子系统
wsl --unregister Arch

## wsl2修改默认安装目录到其他盘 不要把它装到C盘！！！！

wsl -l --all -v
wsl --export Ubuntu-22.04 f:\wsl\Ubuntu.tar
wsl --unregister Ubuntu-22.04
wsl --import Ubuntu-22.04 f:\wsl f:\wsl\Ubuntu.tar --version 2
Ubuntu2204 config --default-user time
del f:\wsl\Ubuntu.tar

## 常用软件及环境配置

=**############以下内容建议全程手机热点###########**=

```bash
sudo add-apt-repository ppa:neovim-ppa/stable
sudo apt update

#替换镜像
https://mirror.tuna.tsinghua.edu.cn/help/ubuntu/
#更新系统
sudo apt update

sudo apt install curl git openssh-server net-tools
#安装zsl
sudo apt install -y zsh
sh -c "$(curl -fsSL https://gitee.com/shmhlsy/oh-my-zsh-install.sh/raw/master/install.sh)"
#使用大佬配置
git clone https://github.com/MarsWang42/My-Vim-Conf.git
#进入库
cd My-Vim-Conf
chmod +x ./setup.sh ./tmux.sh
./setup.sh
source ~/.zshrc
#卸载没用的东西（强迫症）
sudo apt autoremove
#卸载重装neovim 因为人家的配置你不熟悉 最好自己配
sudo apt-get remove neovim
sudo add-apt-repository ppa:neovim-ppa/stable
sudo apt-get update
sudo apt-get install -y neovim
#创建配置文件，这个配置文件是用来配置nvim的·
nvim ~/.config/nvim/init.vim
#去vimawesome 安装插件
#github安装vimplug管理插件
sh -c 'curl -fLo "${XDG_DATA_HOME:-$HOME/.local/share}"/nvim/site/autoload/plug.vim --create-dirs \
       https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim'
#如果443错误 得修改下hosts sudo修改/etc/hosts, 在末尾加入
199.232.68.133 raw.github.com
199.232.28.133 raw.githubusercontent.com

#装好后再打开init.vim 配置文件 添加默认配置

call plug#begin('~/.vim/plugged')
Plug 'vim-airline/vim-airline'
Plug 'vim-airline/vim-airline-themes'
Plug 'mhinz/vim-startify'
Plug 'Yggdroot/indentLine'
Plug 'preservim/nerdtree'
Plug 'crusoexia/vim-monokai'
Plug 'octol/vim-cpp-enhanced-highlight'
Plug 'neoclide/coc.nvim', {'branch': 'release'}
Plug 'Raimondi/delimitMate'
call plug#end()

#退出再载入 然后Pluginstall 安装好 一次不行就多retry几次 务必安好 不然后面没法装clangd



```

#下面是大佬的脚本安的东西 大家自行取舍 
https://github.com/MarsWang42/My-Vim-Conf/blob/master/.config/nvim/init.vim


#特别鸣谢！！！！！！
#本文参考如下！！！！！
https://www.bilibili.com/video/BV1kT411C7vm/?spm_id_from=333.999.0.0&vd_source=54c7f15515681874f0bdf2982482d588

https://www.bilibili.com/video/BV1t54y1R7F3/?spm_id_from=333.999.0.0



# Linux 终端文件管理器 —— ranger

```sudo apt-get install ranger```

h: 返回上一级目录
l: 前往下一级目录
j: 当前目录向下选择
k: 当前目录向上选择
q: 退出
gg: 移动到顶端
G: 移动到底部

S: 在当前目录下打开一个 shell
Shift + S: 在终端中进入当前 ranger 中的路径
?: 打开菜单界面
/: 在当前目录下搜索文件
:: 打开控制台
cd: 打开带着内容 "cd " 的控制台
Ctrl + f: 向下翻页
Ctrl + b: 向上翻页
f: 查找
