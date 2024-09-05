# neovim-tutorial

### Open and Close Files

| Mode | Shortcut | Description                          |
| ---- | -------- | ------------------------------------ |
| `n`  | `I`      | edit at the beginning of the line    |
| `n`  | `A`      | edit at the end of the line          |
|      |          |                                      |
| `n`  | `:q!`    | Exit current buffer without saving   |
| `n`  | `:qa!`   | Exit all open buffers without saving |
| `n`  | `:wqa`   | Save and exit all open buffers       |

### motion

| Mode     | Shortcut（快捷键）               | Description                                                                  |
| -------- | -------------------------------- | ---------------------------------------------------------------------------- |
| n        | split                            | 上下分屏                                                                     |
| n        | vsplit                           | 左右分屏                                                                     |
|          |                                  |                                                                              |
|          |                                  |                                                                              |
| `n`, `v` | `w`                              | One word forward                                                             |
| `n`, `v` | `b`                              | One word backward                                                            |
| `n`, `v` | `^`                              | Beginning of line                                                            |
| `n`, `v` | `$`                              | End of line                                                                  |
| `n`, `v` | `gg`                             | Beginning of file                                                            |
| `n`, `v` | `G`                              | End of file                                                                  |
| `n`, `v` | `{`                              | One paragraph backward                                                       |
| `n`, `v` | `}`                              | One paragraph forward                                                        |
| `n`, `v` | `f` + `[char]`                   | Move to next occurence of `[char]` in current line (Covered in Part 2 video) |
| `n`, `v` | `F` + `[char]`                   | Move to prev occurence of `[char]` in current line (Covered in Part 2 video) |
| `n`, `v` | `Ctrl`+`u`                       | Move Up half a Page (Covered in Part 2 video)                                |
| `n`, `v` | `Ctrl`+`d`                       | Move Down half a Page (Covered in Part 2 video)                              |
| `n`, `v` | `Ctrl`+`b`                       | Move Up a Full Page (Covered in Part 2 video)                                |
| `n`, `v` | `Ctrl`+`f`                       | Move Down a Full Page (Covered in Part 2 video)                              |
| `n`      | `:[num-of-line]` + `Enter`       | Go to a specific line                                                        |
| `n`, `v` | `/[search-item]` + `Enter` + `n` | Find pattern and go to next match                                            |

### Enter `INSERT` Mode from `NORMAL` Mode

| Mode | Shortcut             | Description                                                                        |
| ---- | -------------------- | ---------------------------------------------------------------------------------- |
| `n`  | `i`                  | Insert before cursor                                                               |
| `n`  | `a`                  | Append after cursor                                                                |
| `n`  | `I`                  | Insert at the beginning of the line                                                |
| `n`  | `A`                  | Append at the end of the line                                                      |
| `n`  | `o`                  | Insert to next line                                                                |
| `n`  | `O`                  | Insert to previous line                                                            |
| `n`  | `c` + `[Navigation]` | Delete from before the cursor to `[Navigation]` and insert. Examples are as follow |
| `n`  | `c` + `w`            | Delete from before the cursor to end of current word and insert                    |
| `n`  | `c` + `i` + `w`      | Delete current word and insert                                                     |
| `n`  | `c` + `$`            | Delete from before the cursor to end of the line and insert                        |
| `i`  | `<Esc>`              | Go back to Normal Mode, remap to `jk` recommended                                  |

### Enter `INSERT` Mode from `NORMAL` Mode

| Mode    | Shortcut             | Description                                                                        |
| ------- | -------------------- | ---------------------------------------------------------------------------------- |
| s       |                      | delete currunt word into insert model                                              |
|         |                      |                                                                                    |
| **`n`** | **`I`**              | **Insert at the beginning of the line**                                            |
| **`n`** | **`A`**              | **Append at the end of the line**                                                  |
| **`n`** | **`o`**              | **Insert to next line**                                                            |
| **`n`** | **`O`**              | **Insert to previous line**                                                        |
| `n`     | `c` + `[Navigation]` | Delete from before the cursor to `[Navigation]` and insert. Examples are as follow |
| `n`     | `c` + `w`            | Delete from before the cursor to end of current word and insert                    |
| `n`     | `c` + `i` + `w`      | Delete current word and insert                                                     |
| `n`     | `c` + `$`            | Delete from before the cursor to end of the line and insert                        |
| `i`     | `<Esc>`              | Go back to Normal Mode, remap to `jk` recommended                                  |

### Edit in `NORMAL` Mode

| Mode | Shortcut                                    | Description                                                                                                                                                   |
| ---- | ------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `n`  | `dd`                                        | Delete(cut) current line                                                                                                                                      |
| `n`  | `d` + `[Number]` + `d` Or `[Number]` + `dd` | Delete(cut) following `[Number]` of lines                                                                                                                     |
| `n`  | `d` + `[Navigation]`                        | Delete(cut) from before the cursor to `[Navigation]`, similar to `c` + `[Navigation]` above                                                                   |
| `n`  | `yy`                                        | Yank(copy) current line                                                                                                                                       |
| `n`  | `y` + `[Number]` + `y` Or `[number]` + `yy` | Yank(copy) following `[Number]` of lines                                                                                                                      |
| `n`  | `y` + `[Navigation]`                        | Yank(copy) from before the cursor to `[Navigation]`, similar to `c` + `[Navigation]` above                                                                    |
| `n`  | `p`                                         | Paste from what you delete or yank                                                                                                                            |
| `n`  | `x`                                         | Delete(cut) the character under the cursor                                                                                                                    |
| `n`  | `u`                                         | Undo changes                                                                                                                                                  |
| `n`  | `Ctrl`+`r`                                  | Redo changes                                                                                                                                                  |
| `n`  | `:%s/[foo]/[bar]/g`                         | Find each occurrence of `[foo]` (in all lines), and replace it with `[bar]`. More substitute commands [here](https://vim.fandom.com/wiki/Search_and_replace). |

### `VISUAL` mode shortcuts

| Mode     | Shortcut | Description                                                                |
| -------- | -------- | -------------------------------------------------------------------------- |
| `n`      | `v`      | Enter Visual Character Mode                                                |
| **`n`**  | **`V`**  | **Enter Visual Line Mode** 之后输入：normal即可对选中的这些行进行统一操作  |
| `V-Line` | `>`; `<` | I ent                                                                      |
| `n`      | ctrl q   | Enter Visual Block Mode 然后 操作 然后esc 等价于对选中的这些块做同样的操作 |
| `v`      | `<Esc>`  | Exit Visual Mode, remap to `jk` recommended                                |

## 补充技巧和操作

### 重命名

方法1：

```
:saveas
```

方法2：
:Explore在命令模式下:Explore （我将其实际映射到一个function键，这是非常方便的）。 例如，您可以用R重命名文件，或者用D删除它们。

### [vim多行缩进或缩出](https://www.cnblogs.com/Higgerw/p/16529241.html)

#### 方法一

##### 单行缩进

在要缩进的那一行按下>>, 即连按两下>。

多行缩进

在要缩进的起始行按下n>>，n是要缩进的行数。

##### 单行缩出

在要缩出的那一行按下<<, 即连按两下<。

##### 多行缩出

在要缩出的起始行按下n<<，n是要缩出的行数。

#### 方法二

按Esc，再按下v，进入visual状态，使用键盘的（上、下两个键）选定多行；接下来用 Shift + > 缩进，用 Shfit + < 缩出。

### 批量修改

首先在v-line模式选定你要操作的行 然后输入

：normal 指令

这里的指令是什么。就会对这些行一起做什么

```bash
:s/vivian/sky/    替换当前行第一个 vivian 为 sky
:s/vivian/sky/g    替换当前行所有 vivian 为 sky
:n，$s/vivian/sky/    替换第 n 行开始到最后一行中每一行的第一个 vivian 为 sky
:n，$s/vivian/sky/g    替换第 n 行开始到最后一行中每一行所有 vivian 为 sky
（n 为数字，若 n 为 .，表示从当前行开始到最后一行）

:%s/vivian/sky/（等同于 ：g/vivian/s//sky/）    替换每一行的第一个 vivian 为 sky
:%s/vivian/sky/g（等同于 ：g/vivian/s//sky/g）    替换每一行中所有 vivian 为 sky

:4,7s/old/new #替换4到7行的old为new  4,7这边可替换%代表整个文档
```

#### 全词匹配

如果你输入 “/int”，你也可能找到 “print”。

使用`\<`和`\>`匹配单词的开头和结尾：

```bash
:%s/\<int\>/int/newint
```

#### 不区分大小写

默认是区分大小写的
先输入

:set ignorecase //忽略大小写
进行查找

再输入
:set noignorecase //恢复到大小写敏感

### 光标位置跳转

| n   | crti i | 回到上上个位置                      |
| --- | ------ | ----------------------------------- |
| n   | crtl o | 回到上一个位置无关文件 只看光标位置 |

### 当你没有用sudo 写了一个sudo文件而又不想重写时

：w ! tee %

w表示write

！表示是一个bash指令

tee 是一个可以从stdin接收输入并输出到文件的程序，这里后面接%记录当前文件名

%表示当前文件

强烈推荐这个小游戏Vim大冒险来学习vim！

https://vim-adventures.com/

#大佬的文件看这里：
https://github.com/MarsWang42/My-Vim-Conf

#VimAwesome网站：
https://vimawesome.com/

#Vim Plug Github页面：
https://github.com/junegunn/vim-plug

# 宏操作和多光标

## 录制宏

- 在normal模式下，使用 q+指定寄存器开始录制宏, 可选的寄存器有 数字和大小写字母寄存器
- 再次按下q 结束录制
- 使用`reg [寄存器名称]` 查看指定寄存器中的命令

## 调用宏

- 在normal模式下，使用 @+指定寄存器名称 调用对应寄存器上的宏
- PS: 特殊的调用形式 @@可调用最近调用过的宏 即@a后，可用@@调用a寄存器的宏
- 前面加上数字可以指定调用的次数
