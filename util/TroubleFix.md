# TroubleFix

## [001] pip install -- Unable to create process

### 描述

```bash
$ pip install mycli

Fatal error in launcher: Unable to create process using '"D:\xxx\python312\python.exe"  "D:\xxx\python\python312\Scripts\pip.exe" install mycli': ???????????
```

### 解决

可能是移动了 python 的路径导致的。重装一下 pip 就好了

```bash
python -m pip uninstall pip
python -m ensure pip
```

那么显然也可以一直用 python 调用 pip
