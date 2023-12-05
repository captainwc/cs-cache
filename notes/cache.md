# Vscode配置
## 常用 launch.json 配置参数详解
在使用 launch.json 配置调试环境时，会涉及到多个参数，用于定义调试器的行为和目标执行环境。以下是一些常用的配置参数：

"type"：指定调试器的类型，例如 "node" 表示 Node.js 调试器，"python" 表示 Python 调试器，"java" 表示 Java 调试器等。

"request"：指定调试的请求类型，可以是 "launch"（启动一个新的进程）或 "attach"（附加到已有的进程）。

"name"：为配置提供一个友好的名称，方便识别不同的调试配置。

"program"：用于指定程序的入口文件路径，可以是绝对路径或相对于工作目录的路径。

"args"：传递给程序的命令行参数，以数组形式提供。

"cwd"：指定程序的工作目录，可以是绝对路径或相对于工作目录的路径。

"env"：设置程序运行时的环境变量，以对象形式提供。

"stopOnEntry"：设置为 true 时，在启动后会在入口处停止，等待调试器连接。

"preLaunchTask"：指定在启动调试前运行的任务，通常是一个编译任务。

"postDebugTask"：指定在调试结束后运行的任务，比如清理任务。

"outFiles"：设置输出文件的路径，用于映射源代码和编译后的文件。

"sourceMaps"：控制是否启用源代码映射，可以是 "inline"、"both" 或 "false"。

"sourceMapPathOverrides"：用于根据源代码映射调整文件路径。

"externalConsole"：设置为 true 时，将在外部控制台中运行程序。

"internalConsoleOptions"：控制内部控制台的显示方式，可以是 "neverOpen"、"openOnSessionStart" 或 "openOnFirstSessionStart"。

"showAsyncStacks"：设置为 true 时，在堆栈跟踪中显示异步调用的信息。

"stopOnError"：设置为 true 时，当发生错误时暂停调试。

"smartStep"：设置为 true 时，跳过无需调试的代码。

"skipFiles"：指定不需要调试的文件或文件夹。

"justMyCode"：设置为 true 时，只调试自己的代码。

## 配置例子
### redis
```json
{
    // 使用 IntelliSense 了解相关属性。 
    // 悬停以查看现有属性的描述。
    // 欲了解更多信息，请访问: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "name": "redis-cli",
            "type": "cppdbg",
            "request": "launch",
            "program": "${workspaceFolder}/bin/redis-cli",
            "args": [
                "./redis.conf"
            ],
            "stopAtEntry": false,
            "cwd": "${fileDirname}",
            "environment": [],
            "externalConsole": false,
            "MIMode": "gdb",
            "setupCommands": [
                {
                    "description": "Enable pretty-printing for gdb",
                    "text": "-enable-pretty-printing",
                    "ignoreFailures": true
                }
            ]
        },
        {
            "name": "redis-server",
            "type": "cppdbg",
            "request": "launch",
            "program": "${workspaceFolder}/bin/redis-server",
            "args": [
                "./redis.conf"
            ],
            "stopAtEntry": false,
            "cwd": "${workspaceFolder}",
            "environment": [],
            "externalConsole": false,
            "MIMode": "gdb",
            "setupCommands": [
                {
                    "description": "Enable pretty-printing for gdb",
                    "text": "-enable-pretty-printing",
                    "ignoreFailures": true
                }
            ]
        },
    ]
}
```
### python
[参考](https://xie.infoq.cn/article/183b37b4d36785b3f18f7e5c1)
```json
{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Python: Current File",
      "type": "python",
      "request": "launch",
      "program": "${file}",
      "console": "integratedTerminal"
    },
    "env": {
    	"PYTHONPATH": "",
    }
		"args":[]
  ]
}
```
