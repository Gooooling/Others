# 本文档为VS Code配置C/C++基础环境小教程配套参数、代码集

## P1基础版相关参数

### C/C++ Compile Run ：

- C-cpp-compile-run: C-flags里面填（此处仅为示例，请根据实际情况决定-std的具体标准与是否加-Wextra）：

```
-Wall -Wextra -std=c17 -g
```

- C-cpp-compile-run: Cpp-flags里面填（此处仅为示例，请根据实际情况决定-std的具体标准与是否加-Wextra）：

```
-Wall -Wextra -std=c++20 -g
```

## P2基础加强版&中文乱码相关参数与代码

### C/C++ Compile Run部分

#### 解决中文乱码部分

##### 方法一 (直接加编译参数)：
- **C-cpp-compile-run: C-flags**里面填（此处*仅*为示例，请根据*实际情况*决定**这个-std填啥**与**是否加-Wextra**）：

```
-Wall -Wextra -fexec-charset=GBK -std=c17 -g
```

- **C-cpp-compile-run: Cpp-flags**里面填（此处*仅*为示例，请根据*实际情况*决定**这个-std填啥**与**是否加-Wextra**）：

```
-Wall -Wextra -fexec-charset=GBK -std=c++20 -g
```

##### 方法二（把终端变成utf-8）：

> 找到 **C-cpp-compile-run: Custom-run-prefix** 这个设置项

- 如果你是CMD或1复制这个：
```
chcp 65001 >nul&
```

- 如果你是PS（PowerShell）复制这个：
```
chcp 65001 > $null ; [Console]::OutputEncoding = [System.Text.Encoding]::UTF8 ;
```

### Code Runner部分

#### 普通配置版（此处*仅*为示例，请根据*实际情况*决定**这个-std填啥**与**是否加-Wextra**！！！）

- 默认终端为CMD可以参考复制这个：
``` json
"c": "cd /d \"$dir\" && gcc \"$fileName\" -o \"$fileNameWithoutExt\" -std=c17 -Wall -Wextra && .\\\"$fileNameWithoutExt\"",
```

``` json
"cpp": "cd /d \"$dir\" && g++ \"$fileName\" -o \"$fileNameWithoutExt\" -std=c++20 -Wall -Wextra && .\\\"$fileNameWithoutExt\"",
```

- 默认终端为PS可以参考复制这个：
``` json
"c": "cd $dir && gcc '$fileName' -o '$fileNameWithoutExt' -std=c17 -Wall -Wextra && ./'$fileNameWithoutExt'",
```

``` json
"cpp": "cd $dir && g++ '$fileName' -o '$fileNameWithoutExt' -std=c++20 -Wall 
-Wextra && ./'$fileNameWithoutExt'",
```

#### 解决中文乱码方法一（直接加编译参数）（此处*仅*为示例，请根据*实际情况*决定**这个-std填啥**与**是否加-Wextra**）：

- 默认终端为CMD可以**参考**复制这个：
``` json
"c": "cd /d \"$dir\" && gcc \"$fileName\" -o \"$fileNameWithoutExt\" -std=c17 -Wall -Wextra -fexec-charset=GBK && .\\\"$fileNameWithoutExt\"",
```

``` json
"cpp": "cd /d \"$dir\" && g++ \"$fileName\" -o \"$fileNameWithoutExt\" -std=c++20 -Wall -Wextra -fexec-charset=GBK && .\\\"$fileNameWithoutExt\"",
```

- 默认终端为PS可以**参考**复制这个：
``` json
"c": "cd $dir && gcc '$fileName' -o '$fileNameWithoutExt' -std=c17 -Wall -Wextra -fexec-charset=GBK && ./'$fileNameWithoutExt'",
```

``` json
"cpp": "cd $dir && g++ '$fileName' -o '$fileNameWithoutExt' -std=c++20 -Wall -Wextra -fexec-charset=GBK && ./'$fileNameWithoutExt'",
```

#### 解决中文乱码方法二（修改VS Code的配置）：
> 在设置里搜索terminal.integrated.profiles.windows，点一下**“在settings.json 中编辑”**

- 如果你的默认终端为CMD，大概长这样，args里的一定要一样：
``` json
"Command Prompt": {
            "path": "C:\\WINDOWS\\System32\\cmd.exe",
            "args": [
                "/k",
                "chcp 65001 > nul"
            ],
            "icon": "terminal-cmd"
        },
```

- 如果你的默认终端为PowerShell，请确保：
> 若默认二字为：PowerShell(默认)，大概长这样，args里的一定要一样：

``` json
"PowerShell": {
            "source": "PowerShell",
            "args": [
                "-NoExit",
                "-Command",
                "chcp 65001 > $null ; [Console]::OutputEncoding = [System.Text.Encoding]::UTF8"
            ],
            "icon": "terminal-powershell"
        },
```

> 若默认二字为：Windows PowerShell(默认)，大概长这样，args里的一定要一样：

``` json
"Windows PowerShell": {
            "path": "C:\\WINDOWS\\System32\\WindowsPowerShell\\v1.0\\powershell.exe",
            "args":[
                "-NoExit",
                "-Command",
                "chcp 65001 > $null ; [Console]::OutputEncoding = [System.Text.Encoding]::UTF8"
            ]
        },
```

## 恭喜你！你已经成功完成本次教程的所有内容！期待你在未来能够开心地有所成就！：）