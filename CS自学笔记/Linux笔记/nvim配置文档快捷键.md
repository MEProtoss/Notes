[github: terryma/vim-expand-region](https://github.com/terryma/vim-expand-region)

| 模式   | 键  | 说明         |
| ------ | --- | ------------ |
| visual | v   | 扩大选中范围 |
| visual | V   | 缩小选中范围 |
[github: lfv89/vim-interestingwords](https://github.com/lfv89/vim-interestingwords)

| 模式   | 键  | 说明                 |
| ------ | --- | -------------------- |
| normal | ff  | 高亮/取消高亮 当前词 |
| normal | FF  | 取消高亮 全部词      |

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

[github: mzlogin/vim-markdown-toc](https://github.com/mzlogin/vim-markdown-toc)
:GenTocGFM 在markdown文件头部生成TOC

[github: voldikss/vim-floaterm](https://github.com/voldikss/vim-floaterm)

| 模式   | 键       | 说明                                 |
| ------ | -------- | ------------------------------------ |
| normal | ctrl + t | 打开浮动终端                         |
| normal | ctrl + b | 打开数据库可视化工具(dadbod)         |
| normal | F5       | 根据文件类型启动浮动终端执行当前文件 |

[github: tpope/vim-dadbod](https://github.com/tpope/vim-dadbod)  
 [github: kristijanhusak/vim-dadbod-ui](kristijanhusak/vim-dadbod-ui)

:DBUI 来使用 数据库可视化工具  
 添加链接: let g:dbs = [{ 'name': 'connection_name', 'url': 'mysql://user:password@host:port' }]  
 注意 url内的东西需要url_encode

也可直接 :CALLDB 呼出界面按界面引导 添加链接 链接格式同上

[github: yaocccc/vim-echo](https://github.com/yaocccc/vim-echo)

选中文本后 C: 再下一行添加 console.log(选中的内容) 或 echo $选中的内容 等等等

[github: yaocccc/nvim-foldsign](https://github.com/yaocccc/nvim-foldsign)

在signcolumn显示折叠信息 如果你使用折叠的话

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
<!-- TODO:  -->
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

- [ ] 输出文件格式

```shell
:echo &ft
```

- [ ] 遇到问题怎么办

```shell
help map
```

- [ ] fzf有一个很好用的

```shell
:Helptags
```
