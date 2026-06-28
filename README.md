# ZEBOX Launcher

面向 ZEBOX CS2 社区的 Windows 桌面启动器，使用 WPF 和 .NET 8 开发。

发布版本采用 **框架依赖的单文件** 模式，不在 EXE 中捆绑 .NET 8。用户需要自行安装 .NET 8 Desktop Runtime。

## 功能

- 查看 CS2 社区服务器状态、地图、人数、延迟及玩家列表
- 按服务器模式筛选，并通过 Steam 协议加入服务器
- 自动启动 CS2 并循环尝试加入指定服务器
- 支持国服与国际服启动参数
- 自动检测或手动设置 CS2 安装目录
- 浏览、读取和编辑 CS2/CSGO CFG 文件
- 将 CS2 路径保存到当前用户注册表，重新启动后自动恢复
- 明暗主题、动态主页图片、Toast 状态提示

## 运行环境

- Windows 10/11 64 位
- Steam
- Counter-Strike 2
- [.NET 8 Desktop Runtime x64](https://dotnet.microsoft.com/download/dotnet/8.0)

## 使用方法

1. 下载 `ZedBoxLauncher.exe`。
2. 直接运行启动器。
3. 首次使用时进入“设置”，自动检测或手动选择 CS2 安装目录。
4. 在“服务器”页面查看并加入服务器，或使用自动挤服。
5. 在“CFG”页面选择配置文件进行查看和编辑。

CS2 路径保存在：

```text
HKEY_CURRENT_USER\Software\ZedBoxLauncher
```

程序不会在 EXE 所在目录生成额外的设置文件。

## 从源码运行

需要安装 .NET 8 SDK：

```powershell
dotnet restore
dotnet run
```

## 发布为单 EXE

不包含 .NET 8 运行环境。用户必须先安装 .NET 8 Desktop Runtime x64。

> 单文件版本仅面向 Windows x64。这里需要安装的是 Desktop Runtime，而不是 SDK。

## 技术栈

- .NET 8
- WPF / XAML
- MaterialDesignThemes
- XamlAnimatedGif
- Steam URI
- Source A2S 查询协议

## 项目结构

```text
Models/              数据模型
Services/            Steam、A2S、CFG 和设置服务
ViewModels/          页面状态与绑定逻辑
Resources/           主题、样式、服务器配置和图片资源
Properties/
  PublishProfiles/   单文件发布配置
```

## 注意事项

- 加入服务器依赖 Steam 的 `steam://` 协议。
- CFG 编辑会直接修改所选 CS2 安装目录中的配置文件，请按需自行备份。
- 如果服务器未响应 A2S 查询，启动器会将其显示为离线或查询失败。
