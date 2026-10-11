# C/C++ Compile Run 里的参数
- *C-cpp-compile-run: C-flags*里面填：
```
-Wall -Wextra -std=c17 -Wpedantic
```
- *C-cpp-compile-run: Cpp-flags*里面填：
```
-Wall -Wextra -std=c++20 -Wpedantic
```
>注：-std后的标准请按照实际要求设置。

# Code Runner 里的参数(打开VS Code的设置（Ctrl+,）的json文件，搜索"code-runner.executorMap"，找到对应位置就行)

## 如果你是CMD（可以整体换掉对应行,记得留意后面的逗号）

``` json
        "c": "cd /d \"$dir\" && gcc \"$fileName\" -o \"$fileNameWithoutExt\" -std=c17 -Wall -Wpedantic -Wextra && .\\\"$fileNameWithoutExt\"",
```
``` json
        "cpp": "cd /d \"$dir\" && g++ \"$fileName\" -o \"$fileNameWithoutExt\" -std=c++20 -Wall -Wpedantic -Wextra && .\\\"$fileNameWithoutExt\"",
```

## 如果你是PowerShell（可以整体换掉对应行,记得留意后面的逗号）

``` json
        "c": "cd $dir && gcc '$fileName' -o '$fileNameWithoutExt' -std=c17 -Wall -Wpedantic -Wextra && ./'$fileNameWithoutExt'",
```
``` json
        "cpp": "cd $dir && g++ '$fileName' -o '$fileNameWithoutExt' -std=c++20 -Wall -Wpedantic -Wextra && ./'$fileNameWithoutExt'",
```

>注：-std后的标准请按照实际要求设置。

# 中文乱码方法一

## *使用C/C++ Compile Run者：*
*C-cpp-compile-run: C-flags*里面填：
```
-Wall -Wextra -std=c17 -Wpedantic -fexec-charset=GBK
```
*C-cpp-compile-run: Cpp-flags*里面填：
```
-Wall -Wextra -std=c++20 -Wpedantic -fexec-charset=GBK
```

## *使用Code Runner者：*

### 如果你是CMD（可以整体换掉对应行,记得留意后面的逗号）

``` json
        "c": "cd /d \"$dir\" && gcc \"$fileName\" -o \"$fileNameWithoutExt\" -std=c17 -Wall -Wpedantic -Wextra -fexec-charset=GBK && .\\\"$fileNameWithoutExt\"",
```
``` json
        "cpp": "cd /d \"$dir\" && g++ \"$fileName\" -o \"$fileNameWithoutExt\" -std=c++20 -Wall -Wpedantic -Wextra -fexec-charset=GBK && .\\\"$fileNameWithoutExt\"",
```

### 如果你是PowerShell（可以整体换掉对应行,记得留意后面的逗号）

``` json
        "c": "cd $dir && gcc '$fileName' -o '$fileNameWithoutExt' -std=c17 -Wall -Wpedantic -Wextra -fexec-charset=GBK && ./'$fileNameWithoutExt'",
```
``` json
        "cpp": "cd $dir && g++ '$fileName' -o '$fileNameWithoutExt' -std=c++20 -Wall -Wpedantic -Wextra -fexec-charset=GBK && ./'$fileNameWithoutExt'",
```

# 中文乱码方法二

## 打开VS Code 的设置（Ctrl+,），同样打开json版设置文件（那个settings.json），Ctrl+F搜索‘terminal.integrated.profiles.windows’

> 以下也许是能整体替换该部分的,一定注意好格式，路径等是否跟你的电脑上的VS Code相同，否则请手动复制args并遵守格式塞进去就行，注意*逗号*！！！

``` json
        "PowerShell": {
            "path": "C:\\WINDOWS\\System32\\WindowsPowerShell\\v1.0\\powershell.exe",
            "args": [
                "-NoExit",
                "-Command",
                "chcp 65001 > $null ; [Console]::OutputEncoding = [System.Text.Encoding]::UTF8"
            ],
            "icon": "terminal-powershell"
        },
        "Command Prompt": {
            "path": "C:\\WINDOWS\\System32\\cmd.exe",
            "args": [
                "/k",
                "chcp 65001 > nul"
            ],
            "icon": "terminal-cmd"
        },
```