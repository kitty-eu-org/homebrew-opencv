# homebrew-opencv
Homebrew tap for OpenCV with fixed dependencies

这个仓库维护固定版本的 OpenCV 和其依赖，避免官方 Homebrew 更新导致的兼容性问题。

## 包含的软件

- **opencv**: 4.12.0_9
- **protobuf**: 32.0.1

## 安装方法

### 1. 添加 tap

```bash
brew tap kitty-eu-org/opencv
```

### 2. 安装固定版本的 protobuf

首先需要安装 protobuf 32.0，因为 opencv 4.12.0 依赖这个版本：

```bash
# 如果已经安装了新版本的 protobuf，需要先卸载
brew uninstall protobuf

# 从这个 tap 安装 protobuf 32.0
brew install kitty-eu-org/opencv/protobuf
```

### 3. 安装 opencv

```bash
brew install kitty-eu-org/opencv/opencv
```

## 问题排查

如果遇到 `libprotobuf.32.0.0.dylib` 找不到的错误，请确认：

1. protobuf 32.0 已正确安装：
   ```bash
   brew list protobuf
   ls -la /opt/homebrew/opt/protobuf/lib/libprotobuf.*
   ```

2. 如果需要重新链接：
   ```bash
   brew unlink protobuf && brew link protobuf
   ```
