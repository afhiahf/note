### 在 Windows 终端中构建 Go 项目为 Linux 可执行文件

1. 打开终端（cmd）。

2. 设置环境变量：

```cmd
set GOARCH=amd64
set GOOS=linux
```

3. 构建 Go 项目：

```cmd
go build xxx.go
```

### 提示
- `GOARCH` 指定目标架构，例如 `amd64`。
- `GOOS` 指定目标操作系统，例如 `linux`。
- `go build` 命令将生成适用于指定平台的可执行文件。

