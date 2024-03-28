![nvimyes](https://readme-typing-svg.demolab.com?font=Fira+Code&size=30&pause=1000&color=000000&vCenter=true&width=435&height=45&lines=NVIM+YES)

---

<!-- markdown-toc GitLab -->

- [如何使用](#如何使用)
- [配置结构](#配置结构)
- [lua/profile.lua 通用基础配置说明](#luaprofilelua-通用基础配置说明)
- [lua/keymap.lua 快捷键相关配置说明](#luakeymaplua-快捷键相关配置说明)
- [lua/packinit.lua 插件相关的配置说明](#luapackinitlua-插件相关的配置说明)
- [插件说明以及键位绑定](#插件说明以及键位绑定)
- [markdown键位映射](#markdown键位映射)
- [|i|de|注释|](#ide注释)
- [tmux](#tmux)
- [ranger](#ranger)
- [fzf](#fzf)
- [杂乱的笔记](#杂乱的笔记)
  - [配置入口](#配置入口)

<!-- markdown-toc -->

## 如何使用

1. 将项目clone至 ~/.config/nvim 目录中(注意备份好自己的配置)

   ```plaintext
   cd ~/.config
   git clone https://github.com/yaocccc/nvim
   ```

2. 启动vim 等待自动安装packer(包管理工具、如果你没有安装的话) 会自动安装所有插件

3. 每次修改过lua/packinit.lua 请重启后PackerSync

## 配置结构

```dir
.
├─ lua/                -- LUA配置目录
│  ├─ pack/            -- 各插件的配置目录
│  ├─ G.lua            -- G: Global 封装了lua配置内用到的部分通用方法
│  ├─ keymap.lua       -- 快捷键配置
│  ├─ autocmd.lua      -- 自动命令
│  ├─ packinit.lua     -- 插件配置入口
│  └─ profile.lua      -- 环境变量(各种set)
├─ colors/             -- 样式相关(theme)
├─ ftplugin/           -- 单独文件类型独有的配置
├─ snippets/           -- 代码片段


├─ init.lua            -- 配置入口
├─ coc-settings.json   -- coc配置
└─ README.md           -- README
```

## lua/profile.lua 通用基础配置说明

不额外说明了，有需要直接看 lua/profile.lua 的注释

## lua/keymap.lua 快捷键相关配置说明

| 模式    | 键                  | 说明                                                                               |
| ------- | ------------------- | ---------------------------------------------------------------------------------- |
| normal  | ;                   | :                                                                                  |
| normal  | +                   | 数字自增                                                                           |
| normal  | \_                  | 数字自减                                                                           |
| normal  | ,                   | 重复上一次宏操作将寄存器 q 中的内容执行。                                          |
| normal  | ctrl + j            | 从, 处打断当前行                                                                   |
| normal  | \                   | 清除当前搜索词高亮                                                                 |
| normal  | \w                  | 开启/关闭wrap显示                                                                  |
| normal  | backspace           | 删除当前词并插入                                                                   |
| insert  | ctrl + h(backspace) | 删除内至词首                                                                       |
| insert  | ctrl + z            | 撤销最后修改并退出编辑                                                             |
| command | ctrl + a            | 行首输入                                                                           |
| command | ctrl + e            | 行尾输入                                                                           |
| all     | ctrl + s            | 进入替换模式                                                                       |
| normal  | S                   | save                                                                               |
| normal  | W                   | close buffer                                                                       |
| normal  | Q                   | quit windows                                                                       |
| normal  | R                   | 重载配置                                                                           |
| normal  | >>                  | 将代码块右移                                                                       |
| normal  | <<                  | 将代码块左移                                                                       |
| visual  | > or tab            | 将代码块右移                                                                       |
| visual  | < or shift + tab    | 将代码块左移                                                                       |
| all     | shift + 方向        | 选中文本(类似于在其他编辑器的体验)                                                 |
| all     | q + shift + 方向    | 快速移动                                                                           |
| all     | ctrl + u            | 清空本行                                                                           |
| all     | alt + up/down       | 上下移动当前行/块                                                                  |
| all     | alt + o             | 下方新起一行                                                                       |
| all     | alt + O             | 上方新起一行                                                                       |
| normal  | sv                  | 左右分屏                                                                           |
| normal  | sp                  | 上下分屏                                                                           |
| normal  | sc                  | 关闭当前窗口                                                                       |
| normal  | so                  | 关闭其他所有窗口                                                                   |
| normal  | s + 方向            | 聚焦到对应窗口                                                                     |
| normal  | ctrl + space        | 切换窗口                                                                           |
| normal  | s=                  | 将窗口大小置为相ss同                                                               |
| normal  | s,                  | 窗口减小                                                                           |
| normal  | s.                  | 窗口增大                                                                           |
| normal  | alt,/.              | 上/下窗口切换                                                                      |
| normal  | ss                  | 切换到下个buffer                                                                   |
| all     | alt + left or right | 左右跳转buffer                                                                     |
| all     | F5                  | 一键运行当前文件                                                                   |
| normal  | --                  | 折叠/反折叠                                                                        |
| visual  | -                   | 折叠选中内容                                                                       |
| normal  | space               | 在行首 第一个非空字符 行尾 跳转                                                    |
| visual  | =                   | 格式化选中内容                                                                     |
| visual  | t                   | 驼峰和下划线转换                                                                   |
|         |                     |                                                                                    |
| i       | alt d/r             | 删除当前词汇 并复制到剪贴板并继续输入/删除光标所在的单词并替换为当前寄存器中的文本 |
| n       | alt d/r             | 删除当前词汇 并保持normal mode / 更改光标所在的单词，并将光标移动到插入模式中      |
| n       | alt a               | 选中全文 选中{ 复制全文                                                            |
| n       | alt s               | 选中全文 选中{ 复制全文                                                            |
| i       | ctrl a              | 行尾输入                                                                           |
| i       | ctrl i              | 行首输入                                                                           |
| i       | ctrl e              | 逐字拷贝下一行？                                                                   |
| i       | ctrl h              | 删除当前单词                                                                       |
| n       | Y                   | 复制到行尾                                                                         |
| i       | s-right             | 当前词尾                                                                           |
| i       | ctrl-d              | 删除当前光标位置的字符                                                             |
| i       | ctrl-k              | 退格                                                                               |
| i       | ctrl-l              | enter                                                                              |
|         |                     |                                                                                    |
|         |                     |                                                                                    |
|         |                     |                                                                                    |
|         |                     |                                                                                    |
|         |                     |                                                                                    |
|         |                     |                                                                                    |
|         |                     |                                                                                    |
|         |                     |                                                                                    |
|         |                     |                                                                                    |
|         |                     |                                                                                    |
|         |                     |                                                                                    |

PS: 如果需要格式化js和ts代码，请手动安装: npm i js-beautify -g

## lua/packinit.lua 插件相关的配置说明

## 插件说明以及键位绑定

<details>
  <summary style="cursor: pointer; text-decoration:underline; color: #2AD;">dstein64/vim-startuptime -- 启动时间分析</summary>

[github: dstein64/vim-startuptime](https://github.com/dstein64/vim-startuptime)

:StartupTime

</details>

<details>
  <summary style="cursor: pointer; text-decoration:underline; color: #2AD;">terryma/vim-expand-region -- 快速选中文本</summary>

[github: terryma/vim-expand-region](https://github.com/terryma/vim-expand-region)

| 模式   | 键  | 说明         |
| ------ | --- | ------------ |
| visual | v   | 扩大选中范围 |
| visual | V   | 缩小选中范围 |

</details>

<details>
  <summary style="cursor: pointer; text-decoration:underline; color: #2AD;">lfv89/vim-interestingwords -- 高亮关键词</summary>

[github: lfv89/vim-interestingwords](https://github.com/lfv89/vim-interestingwords)

| 模式   | 键  | 说明                 |
| ------ | --- | -------------------- |
| normal | ff  | 高亮/取消高亮 当前词 |
| normal | FF  | 取消高亮 全部词      |

</details>

<details>
  <summary style="cursor: pointer; text-decoration:underline; color: #2AD;">mg979/vim-visual-multi -- 虚拟多光标</summary>

[gihub: **mg979/vim-visual-multi**](https://github.com/mg979/vim-visual-multi)  
 [bilibili视频介绍: BV1uF411c7Ro](https://www.bilibili.com/video/BV1uF411c7Ro)

建议到对应的仓库仔细看文档 、

| 模式   | 键                | 说明                                 |
| ------ | ----------------- | ------------------------------------ |
| normal | ctrl + up/down    | 上下添加虚拟光标(normal模式)         |
| normal | ctrl + left/right | 虚拟光标左右扩选(visual模式)         |
| normal | ctrl + d          | 所有`当前词`添加虚拟光标(visual模式) |
| normal | ctrl + x          | 当前字符添加虚拟光标(normal模式)     |
| normal | ctrl + w          | 添加当前词首(normal模式)             |
| all    | ctrl + n/p        | 添加下/上一个当前词到虚拟光标        |
| all    | q                 | 移除当前光标位置下的虚拟光标         |
| normal | tab               | 切换到visual模式                     |
| visual | tab               | 切换到normal模式                     |

</details>

<details>
  <summary style="cursor: pointer; text-decoration:underline; color: #2AD;">iamcco/markdown-preview.nvim -- md 预览插件</summary>

[github: iamcco/markdown-preview.nvim](https://github.com/iamcco/markdown-preview.nvim)

guide: 如果无法使用 请

1. 修改 lua/pack/markdown.lua 中的 G.g.mkdp_browser 去掉或者修改成自己使用的浏览器
2. cd ~/.local/share/nvim/site/pack/packer/opt/markdown-preview.nvim/app && yarn

| 模式   | 键  | 说明                 |
| ------ | --- | -------------------- |
| normal | F5  | 在浏览器预览markdown |

</details>

<details>
  <summary style="cursor: pointer; text-decoration:underline; color: #2AD;">mzlogin/vim-markdown-toc -- md 生成目录</summary>

[github: mzlogin/vim-markdown-toc](https://github.com/mzlogin/vim-markdown-toc)

:GenTocGFM 在markdown文件头部生成TOC

</details>

<details>
  <summary style="cursor: pointer; text-decoration:underline; color: #2AD;">voldikss/vim-floaterm -- 悬浮终端插件</summary>

[github: voldikss/vim-floaterm](https://github.com/voldikss/vim-floaterm)

| 模式   | 键       | 说明                                 |
| ------ | -------- | ------------------------------------ |
| normal | ctrl + t | 打开浮动终端                         |
| normal | ctrl + b | 打开数据库可视化工具(dadbod)         |
| normal | F5       | 根据文件类型启动浮动终端执行当前文件 |

</details>

<details>
  <summary style="cursor: pointer; text-decoration:underline; color: #2AD;">tpope/vim-dadbod -- 数据库可视化工具</summary>

[github: tpope/vim-dadbod](https://github.com/tpope/vim-dadbod)  
 [github: kristijanhusak/vim-dadbod-ui](kristijanhusak/vim-dadbod-ui)

:DBUI 来使用 数据库可视化工具  
 添加链接: let g:dbs = [{ 'name': 'connection_name', 'url': 'mysql://user:password@host:port' }]  
 注意 url内的东西需要url_encode

也可直接 :CALLDB 呼出界面按界面引导 添加链接 链接格式同上

</details>

<details>
  <summary style="cursor: pointer; text-decoration:underline; color: #2AD;">junegunn/fzf.vim -- 文本/文件搜索</summary>

[github: **junegunn/fzf.vim**](https://github.com/junegunn/fzf.vim)

注意要配合ag使用，请自己手动安装: the_silver_searcher fd bat

| 模式   | 键       | 说明                 |
| ------ | -------- | -------------------- |
| normal | ctrl + a | Ag搜索(全局文本搜索) |
| normal | ctrl + l | 当前buffer文本搜索   |
| normal | ctrl + p | 全局文件搜索         |
| normal | ctrl + g | git变更文件搜索      |
| normal | ctrl + h | 历史文件搜索         |
| fzf中  | ctrl + / | 启动/关闭 预览       |
| fzf中  | ctrl + n | 下一个搜索词         |
| fzf中  | ctrl + p | 上一个搜索词         |

</details>

<details>
  <summary style="cursor: pointer; text-decoration:underline; color: #2AD;">gelguy/wilder.nvim -- 弹出式的命令行</summary>

[github: gelguy/wilder.nvim](https://github.com/gelguy/wilder.nvim)

</details>

<details>
  <summary style="cursor: pointer; text-decoration:underline; color: #2AD;">kyazdani42/nvim-tree.lua -- 文件管理器</summary>

[github: kyazdani42/nvim-tree.lua](https://github.com/kyazdani42/nvim-tree.lua)

| 模式        | 键     | 说明                                |
| ----------- | ------ | ----------------------------------- |
| normal      | T      | 打开/关闭 nvim-tree                 |
| nvim-tree内 | a/A    | 新建文件或文件夹                    |
| nvim-tree内 | r      | 重命名                              |
| nvim-tree内 | W      | 关闭所有打开的目录                  |
| nvim-tree内 | <left> | 关闭当前目录                        |
| nvim-tree内 | <bs>   | 回退到上级目录                      |
| nvim-tree内 | P      | cd到选中目录                        |
| nvim-tree内 | H      | 显示/隐藏 .文件                     |
| nvim-tree内 | I      | 显示/隐藏 忽略文件(gitignore等)     |
| nvim-tree内 | d      | 删除文件/文件夹                     |
| nvim-tree内 | x      | 剪切文件/文件夹到剪切板             |
| nvim-tree内 | c      | 复制文件/文件夹到剪切板             |
| nvim-tree内 | p      | 从剪切板粘贴                        |
| nvim-tree内 | y      | 复制文件名                          |
| nvim-tree内 | ?      | 查看帮助                            |
| nvim-tree内 | C      | 若当前查看的文件为外部文件 cd到目录 |

</details>

<details>
  <summary style="cursor: pointer; text-decoration:underline; color: #2AD;">nvim-treesitter/nvim-treesitter -- 文本分析插件</summary>

[github: nvim-treesitter/nvim-treesitter](https://github.com/nvim-treesitter/nvim-treesitter)

没啥好说明的 用就完了

可以用 H 快捷键看高亮组 然后到 lua/pack/tree-sitter.lua 中修改对应的样式  
 R刷新高亮

</details>

<details>
  <summary style="cursor: pointer; text-decoration:underline; color: #2AD;">neoclide/coc.nvim -- coc</summary>

[github: neoclide/coc.nvim](https://github.com/neoclide/coc.nvim)

**建议到对应的仓库看一下**

- coclist marketplace 有一个插件市场

  全局的插件列表 lua/pack/coc.lua -- G.g.coc_global_extensions = {...} 按需添加

  | 模式   | 键  | 说明                      | 对应的coc插件  |
  | ------ | --- | ------------------------- | -------------- |
  | normal | gd  | 跳转到定义                | coc            |
  | normal | gy  | 跳转到类型                | coc            |
  | normal | gr  | 跳转到实现                | coc            |
  | normal | K   | 查看文档                  | coc            |
  | normal | c-e | 查看诊断列表              | coc            |
  | normal | F2  | 重命名                    | coc            |
  | normal | F4  | 关闭/开启coc              | coc            |
  | normal | c-e | 查看诊断列表              | coc            |
  | normal | mm  | 翻译当前词                | coc-translator |
  | normal | F9  | 编辑当前文件类型的snippet | coc-snippets   |
  | normal | (   | 上一处修改                | coc-git        |
  | normal | )   | 下一处修改                | coc-git        |
  | normal | C   | 显示当前行提交记录        | coc-git        |
  | normal | \g  | 开启/关闭 git blame 显示  | coc-git        |
  | visual | if  | 选中func内                | coc            |
  | visual | af  | 选中func                  | coc            |
  | visual | ic  | 选中class内               | coc            |
  | visual | ac  | 选中class                 | coc            |

</details>

<details>
  <summary style="cursor: pointer; text-decoration:underline; color: #2AD;">github/copilot.vim -- github copilot</summary>

[github: github/copilot.vim](https://github.com/github/copilot.vim)

| 模式   | 键         | 说明        |
| ------ | ---------- | ----------- |
| insert | right      | 接受建议    |
| insert | ctrl + ]   | 取消建议    |
| insert | alt + [或] | 上/下个建议 |

</details>

<details>
  <summary style="cursor: pointer; text-decoration:underline; color: #2AD;">yaocccc/nvim-lines.lua -- 状态栏/标签栏</summary>

[github: yaocccc/nvim-lines.lua](https://github.com/yaocccc/nvim-lines.lua)

没啥好说明的 用就完了

</details>

<details>
  <summary style="cursor: pointer; text-decoration:underline; color: #2AD;">yaocccc/nvim-hlchunk -- {}区间高亮</summary>

[github: yaocccc/nvim-hlchunk](https://github.com/yaocccc/nvim-hlchunk)

没啥好说明的 用就完了

</details>

<details>
  <summary style="cursor: pointer; text-decoration:underline; color: #2AD;">yaocccc/vim-surround -- 快速操作({["'`等的</summary>

[github: yaocccc/vim-surround](https://github.com/yaocccc/vim-surround)

选中文本后 再使用 " ' { ( 等 可以将文本包裹起来  
 ds": 删除包裹的"" 其他的相同  
 ys": 用""将当前词包裹起来  
 cs"{: 用{}替换掉""

</details>

<details>
  <summary style="cursor: pointer; text-decoration:underline; color: #2AD;">yaocccc/vim-comment -- 快速注释</summary>

[github: yaocccc/vim-comment](https://github.com/yaocccc/vim-comment)

普通模式 ??: 行注释当前行
选中文本后 /: 行注释选中内容
选中文本后 ?: 块注释选中内容

**以上操作 可以用相同的操作逆转 (??行注释 ??取消行注释)**

</details>

<details>
  <summary style="cursor: pointer; text-decoration:underline; color: #2AD;">yaocccc/vim-fcitx2en -- 退出insert模式时 自动切换到英文</summary>

[github: yaocccc/vim-fcitx2en](https://github.com/yaocccc/vim-fcitx2en)

</details>

<details>
  <summary style="cursor: pointer; text-decoration:underline; color: #2AD;">yaocccc/vim-echo -- 根据文件名或文件类型快速echo、print、console.log</summary>

[github: yaocccc/vim-echo](https://github.com/yaocccc/vim-echo)

选中文本后 C: 再下一行添加 console.log(选中的内容) 或 echo $选中的内容 等等等

</details>

<details>
  <summary style="cursor: pointer; text-decoration:underline; color: #2AD;">yaocccc/nvim-foldsign -- 在signcolumn显示折叠信息</summary>

[github: yaocccc/nvim-foldsign](https://github.com/yaocccc/nvim-foldsign)

在signcolumn显示折叠信息 如果你使用折叠的话

</details>

## markdown键位映射

| 模式 | 键           | 说明                           |
| ---- | ------------ | ------------------------------ |
| i    | ,f / ctrl-e  | next anchor<++>                |
| i    | ,w           | next anchor and enter new line |
| i    | ,n           | —                              |
| i    | ,l           | --------                       |
| i    | ,b           | \*\*\*\*                       |
| i    | ,h           | ====                           |
| i    | ,s           | ~~~~                           |
| i    | ,i           | \*\*                           |
| i    | ,d           | ``                             |
| i    | ,c           | code                           |
| i    | ,number      | title                          |
| i    | ,m/td        | - [ ]                          |
| i    | ,p           |                                |
| i    | ,a           |                                |
| i    | pic          | picture                        |
| i    | td           | task                           |
| i    | td           | > task                         |
| i    | tdd          | > > > task                     |
| i    | tddd         | > > > task                     |
| i    | ss           | task start:                    |
| i    | dd           | task deadline:                 |
| i    | ref          | ref                            |
| i    | mer          | mermaid                        |
| i    | sub          | subgraphy                      |
| i    | classDiagran | classDiagran                   |
| i    | class        | class                          |
| i    | table"n"     | create a table with n columns  |
| i    | details      | details~                       |
| i    | sp           | spaces~                        |
| i    | de           | 注释                           |

---

## tmux

- 基本指令

```bash
tmux new -s <session-name> 新建会话
tmux detach 或者Ctrl+b d 分离会话，命令执行后，就会退出当前 Tmux 窗口，但是会话和里面的进程仍然在后台运行。
tmux ls 查看当前所有的 Tmux 会话
tmux attach -t <session-name> 重新接入某个已存在的会话
tmux kill-session -t <session-name> 杀死某个会话
tmux switch -t <session-name> 切换会话
tmux rename-session -t 0 <new-name> 重命名会话
```

- 会话快捷键

1. Ctrl+b d：分离当前会话。
2. Ctrl+b s：列出所有会话。
3. Ctrl+b $：重命名当前会话。

- 最简操作流程

1. 新建会话tmux new -s my_session。
2. 在 tmux 窗口运行所需的程序。
3. 按下快捷键Ctrl+b d将会话分离。
4. 下次使用时，重新连接到会话tmux attach-session -t my_session。

- 一些其他命令

```bash
# 列出所有快捷键，及其对应的 Tmux 命令
$ tmux list-keys

# 列出所有 Tmux 命令及其参数
$ tmux list-commands

# 列出当前所有 Tmux 会话的信息
$ tmux info

# 重新加载当前的 Tmux 配置
$ tmux source-file ~/.tmux.conf

```

| snippets                 | function                      |
| ------------------------ | ----------------------------- |
| prefix m                 | 切换鼠标模式                  |
| prefix +                 | 最大化任何窗格到新窗口        |
| prefix r                 | 重新加载                      |
| C-l                      | 清屏和清除历史记录            |
| prefix C-h 并 prefix C-l | 浏览窗口                      |
| prefix tab               | 回到上一个活动窗口            |
| prefix -                 | 垂直分割                      |
| prefix \_                | 竖直分割                      |
| prefix h/j/k/l           | 切换窗口                      |
| prefix H/J/K/L           | 调整窗口大小                  |
| prefix </>               | 交换窗口                      |
| prefix U                 | 启动Urlview                   |
| prefix F                 | 启动facebook pathpicker       |
| prefix Enter             | 复制模式                      |
| prefix b                 | 粘贴缓存区                    |
| prefix p                 | 选择、粘贴                    |
| v                        | 选择、visual模式              |
| C-v                      | 在visual和visual-block 中切换 |
| H                        | beginning of the line         |
| L                        | end of the line               |
| y                        | 将选择复制到顶部粘贴缓冲区    |
| escappe                  | cancel current operation      |

## ranger

| 按键                      | 功能                                                   |
| ------------------------- | ------------------------------------------------------ |
| [ ]                       | 移动父文件夹                                           |
| H                         | 历史记录退回                                           |
| L                         | 历史记录反跳回                                         |
| o s/c/n                   | 排序 按照大小、修改日期、文件名                        |
| /                         | 搜索文件                                               |
| zf                        | 过滤                                                   |
| q                         | 退出ranger                                             |
| S                         | 进入目录                                               |
| c-f                       | fzf                                                    |
| yp                        | yank path                                              |
| yn                        | yank name                                              |
| y.                        | yank filename without file extension                   |
| V                         | 创建文件                                               |
| mkcd                      | 创建文件夹                                             |
| cw                        | 重命名                                                 |
| a/I/A                     | 重命名                                                 |
| v                         | 全选                                                   |
| space                     | 选择                                                   |
| ：bulkrename              | 然后进入visual block模式 进行输入操作后esc即可统一修改 |
| dd/yy/pp                  |                                                        |
| dD                        | 删除                                                   |
| dU                        | 查看文件夹大小                                         |
| w                         | 任务管理器                                             |
| ：compress                | 压缩                                                   |
| ：extracthere             | 解压                                                   |
| cp                        | 制作pdf                                                |
| ytv(shell youtube-dl -ic) | 下载YouTube视屏                                        |
| back/zh                   | 显示隐藏文件                                           |
|                           |                                                        |

## fzf

| 按键 | 功能 |
| ---- | ---- |
| fzf  |      |
|      |      |
|      |      |
|      |      |
|      |      |
|      |      |
|      |      |
|      |      |
|      |      |

## 杂乱的笔记

### 配置入口

- 配置入口 ：init.lua

- vim 和lua的替换

![image-20230407114521540](https://cdn.jsdelivr.net/gh/MEProtoss/cloudimg/My%20Collectionsimage-20230407114521540.png)

![image-20230407114620158](https://cdn.jsdelivr.net/gh/MEProtoss/cloudimg/My%20Collectionsimage-20230407114620158.png)

![image-20230510100057444](https://cdn.jsdelivr.net/gh/MEProtoss/cloudimg/My%20Collectionsimage-20230510100057444.png)

![image-20230510100128221](https://cdn.jsdelivr.net/gh/MEProtoss/cloudimg/My%20Collectionsimage-20230510100128221.png)

b:buffer

o:设置变量

g ：globe

```lua
echo expand('%') -----vim.fn.expand('%')
```

- 常用指令

  pack

  packercompile

  packerSync

- nvim +PackerSync 加号能传进去一个命令

  ![image-20230407120248958](https://cdn.jsdelivr.net/gh/MEProtoss/cloudimg/My%20Collectionsimage-20230407120248958.png)

  插件的配置文件在packer目录下

  config里的代码在插件载入后执行

  setup里的代码载入前执行

  ft（filetype） 只对指定类型生效

  event 当。。。时才载入

  cmd 只有某些命令使用时才载入

  测试启动时间
  nvim +StartupTime

-

- [ ] 输出文件格式

```shell
:echo &ft
```

- [ ] 插件哪里找
      awesome-neovim

- [ ] 遇到问题怎么办

```shell
help map
```

- [ ] fzf有一个很好用的

```shell
:Helptags
```

- [ ] lua 学习
      nvim-lua-guide

## nvim-new 的快捷键

- buffer
- <A-q> 关闭当前buffer
- <A-S-q> 关闭当前窗口

- split buffer vertically N <C-w>v
- split buffer horizontally N <C-w>s
