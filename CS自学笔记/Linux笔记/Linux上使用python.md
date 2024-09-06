## linux 中创建python虚拟环境和切换虚拟环境的办法

- 安裝venv

```bash
sudo pacman -S python-virtualenv
```

- 在專案目錄用Python 3.8建立虛擬環境venv

```bash
python3.8 -m venv [虚拟环境的名字]
```

- 進入虛擬環境

```bash
source [虚拟环境的名字]/bin/activate
```

## linux中命令行识别不到python模块

### 修改 PYTHONPATH

- 通过修改 PYTHONPATH 环境变量来告诉 Python 在哪里查找模块。在 Unix-like 系统中，你可以在命令行中这样做：

```bash
export PYTHONPATH="${PYTHONPATH}:/path/to/your/module"
```

- 使用包来组织模块：如果你有多个相关的模块，可以将它们组织成一个包。在包的目录中创建一个 __init__.py 文件，然后可以在其他文件中使用相对导入来引用包内的模块
