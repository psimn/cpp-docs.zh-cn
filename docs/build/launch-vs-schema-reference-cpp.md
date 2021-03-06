---
title: 启动. 与 json 架构引用（C++）
ms.date: 08/20/2019
helpviewer_keywords:
- launch.vs.json file [C++]
ms.openlocfilehash: 5d8f657dda58d581ccc3441a777fdf31470ef25f
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518226"
---
# <a name="launchvsjson-schema-reference-c"></a>启动. 与 json 架构引用（C++）

使用*启动. vs json*文件配置调试参数。 来创建文件。 右键单击 "**解决方案资源管理器**中的可执行文件，然后选择"**调试和启动设置**"。 选择与你的项目最匹配的选项，然后使用以下属性根据需要修改配置。 有关调试 CMake 项目的详细信息，请参阅[Configure CMake 调试会话](/cpp/build/configure-cmake-debugging-sessions)。

## <a name="default-properties"></a>默认属性

||||
|-|-|-|
|**Property**|**Type**|**描述**|
|`name`|string|指定调试目标下拉列表中的条目的名称。|
|`type`|string|指定项目是 dll 还是 .exe （默认为 .exe）|
|`project`|string|指定项目文件的相对路径。|
|`projectTarget`|string|指定在生成 `project`时调用的可选目标。 此 `projectTarget` 必须已存在，并且与**调试目标**下拉列表中的名称匹配。|
|`debugType`|string|根据代码类型（本机、托管或混合）指定调试模式。 如果未设置此参数，则会自动检测到此参数。 允许的值： "本机"、"托管"、"mixed"。|
|`inheritEnvironments`|数组|指定从多个源继承的一组环境变量。 可以在文件中定义一些变量（如*CMakeSettings*或*cppproperties.json* ），并使它们可用于调试上下文。  **Visual Studio 16.4：** ：使用 `env.VARIABLE_NAME` 语法按目标指定环境变量。 若要取消设置某个变量，请将其设置为 "null"。|
|`args`|数组|指定传递给已启动程序的命令行参数。|
|`currentDir`|string|指定生成目标的完整目录路径。 如果未设置此参数，则会自动检测到此参数。|
|`noDebug`|boolean|指定是否调试已启动的程序。 如果未指定此参数，则默认值为 `false`。|
|`stopOnEntry`|boolean|指定是否在进程启动和调试器附加时立即中断。 此参数的默认值为 `false`。|
|`remoteMachine`|string|指定启动程序的远程计算机的名称。|
|`env`|数组| 指定自定义环境变量的键值列表。 env： {"myEnv"： "myVal"}。|
|`portName`|string|指定连接到正在运行的进程时的端口名称。|
|`buildConfigurations`|数组| 指定应用配置的生成模式的名称的键值对。 例如，根据所选生成模式 `Debug` 或 `Release` 以及要使用的配置。

## <a name="c-linux-properties"></a>C++Linux 属性

||||
|-|-|-|
|**Property**|**Type**|**描述**|
|`program`|string|远程计算机上的程序可执行文件的完整路径。 当使用 CMake 时，宏 `${debugInfo.fullTargetPath}` 可以用作此字段的值。|
|`processId`|整数|要将调试器附加到的可选进程 ID。|
|`sourceFileMap`|对象|传递给调试引擎的可选源文件映射。 格式： `{ "\<Compiler source location>": "\<Editor source location>" }` 或 `{ "\<Compiler source location>": { "editorPath": "\<Editor source location>", "useForBreakpoints": true } }`。 示例：`{ "/home/user/foo": "C:\\foo" }` 或 `{ "/home/user/foo": { "editorPath": "c:\\foo", "useForBreakpoints": true } }`。 请参阅[源文件映射选项](#source_file_map_options)。|
|`additionalProperties`|string|其中一个 sourceFileMapOptions。 （请参阅下文。）|
|`MIMode`|string|指示 MIDebugEngine 将连接到的支持 MI 的控制台调试器的类型。 允许的值为 "gdb"、"lldb"。|
|`args`|数组|传递给程序的命令行参数。|
|`environment`|数组|要添加到程序的环境中的环境变量。 示例： [{"name"： "squid"，"value"： "clam"}]。|
|`targetArchitecture`|string|调试对象的体系结构。 如果未设置此参数，则会自动检测到此参数。 允许的值为 x86、arm、arm64、mips、x64、amd64、x86_64。|
|`visualizerFile`|string|调试此进程时要使用的 natvis 文件。 此选项与 GDB 打印不兼容。 如果使用此设置，请参阅 "showDisplayString"。|
|`showDisplayString`|boolean|指定 visualizerFile 时，showDisplayString 将启用显示字符串。 启用此选项可能会导致调试过程中的性能降低。|
|`remoteMachineName`|string|托管 gdb 的远程 Linux 计算机和要调试的程序。 使用连接管理器添加新的 Linux 计算机。 当使用 CMake 时，宏 `${debugInfo.remoteMachineName}` 可以用作此字段的值。|
|`cwd`|string|远程计算机上的目标的工作目录。 当使用 CMake 时，宏 `${debugInfo.defaultWorkingDirectory}` 可以用作此字段的值。 除非在*cmakelists.txt*文件中重写，否则默认值为远程工作区根目录。|
|`miDebuggerPath`|string|已启用 MI 的调试器的路径（如 gdb）。 如果未指定，它将首先搜索调试器的路径。|
|`miDebuggerServerAddress`|string|要连接到的已启用 MI 的调试器服务器的网络地址。 示例： localhost：1234。|
|`setupCommands`|数组|为了设置基础调试器，要执行的一个或多个 GDB/LLDB 命令。 示例：`"setupCommands": [ { "text": "-enable-pretty-printing", "description": "Enable GDB pretty printing", "ignoreFailures": true }]`。 请参阅[启动安装程序命令](#launch_setup_commands)。|
|`customLaunchSetupCommands`|数组|如果提供了此值，则会替换用于用一些其他命令启动目标的默认命令。 例如，为了附加到目标进程，这可以是 "-target-attach"。 空命令列表将启动命令替换为 nothing，这在将调试器作为命令行选项提供的启动选项时非常有用。 示例：`"customLaunchSetupCommands": [ { "text": "target-run", "description": "run target", "ignoreFailures": false }]`。|
|`launchCompleteCommand`|string|在调试程序完全设置后要执行的命令，以使目标进程得以运行。 允许的值为 "exec-run"、"exec-continue"、"None"。 默认值为 "exec-run"。|
|`debugServerPath`|string|调试要启动的服务器的可选完整路径。 默认值为 null。|
|`debugServerArgs`|string|可选的 debug 服务器参数。 默认值为 null。|
|`filterStderr`|boolean|在 stderr 流中搜索服务器启动模式，并将 stderr 记录到调试输出。 默认为 `false`。|
|`coreDumpPath`|string|指定程序的核心转储文件的可选完整路径。 默认值为 null。|
externalConsole|boolean|如果为 true，则为调试对象启动控制台。 如果 `false`，则不会启动任何控制台。 默认为 `false`。 注意：在某些情况下，出于技术方面的原因，将忽略此选项。|
|`pipeTransport`|string|出现这种情况时，它会告知调试器使用另一个可执行文件作为管道连接到远程计算机，以便在 Visual Studio 和启用了 MI 的调试程序（如 gdb）之间中继标准输入/输出。 允许的值：一个或多个[管道传输选项](#pipe_transport_options)。|


## <a name="launch_setup_commands"></a>启动安装程序命令

与 `setupCommands` 属性一起使用：

||||
|-|-|-|
|`text`|string|要执行的调试器命令。|
|`description`|string|命令的可选说明。|
|`ignoreFailures`|boolean|如果为 true，则应忽略命令中的失败。 默认为 `false`。|

## <a name = "pipe_transport_options"></a>管道传输选项

与 `pipeTransport` 属性一起使用：

||||
|-|-|-|
|`pipeCwd`|string|管道程序工作目录的完全限定路径。|
|`pipeProgram`|string|要执行的完全限定的管道命令。|
|`pipeArgs`|数组|传递给管道程序配置连接的命令行参数。|
|`debuggerPath`|string|目标计算机上调试程序的完整路径，例如/usr/bin/gdb。|
|`pipeEnv`|对象|传递给管道程序的环境变量。|
|`quoteArgs`|boolean|如果各个参数包含字符（如空格或制表符），是否应将其括起来？ 如果 `false`，则调试器命令将不再自动加上引号。 默认值为 `true`。|

## <a name="source_file_map_options"></a>源文件映射选项

与 `sourceFileMap` 属性一起使用：

||||
|-|-|-|
|`editorPath`|string|编辑器要查找的源代码的位置。|
|`useForBreakpoints`|boolean|设置断点时，应使用此源映射。 如果 `false`，则仅使用文件名和行号来设置断点。 如果 `true`，则只有在使用此源映射时，才会使用文件和行号的完整路径来设置断点。 否则，在设置断点时，只会使用文件名和行号。 默认值为 `true`。|
