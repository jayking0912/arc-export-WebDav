# Arc 浏览器书签同步工具

## 概述

这个项目提供了一个将 Arc 浏览器的固定标签页转换为标准 HTML 书签文件的工具，并支持将书签同步到 WebDAV 服务器（如坚果云）。这些书签可以被导入到任何网页浏览器中，并通过同步插件实现多浏览器间的书签同步。

该工具解决了 Arc 浏览器缺乏书签导出和同步功能的问题。

## 使用步骤

### 1. 下载仓库

```bash
git clone https://github.com/jayking0912/arc-export-WebDav.git
cd arc-export-WebDav
```

### 2. 配置 WebDAV 信息

编辑 `webdav.ini` 文件，填写你的 WebDAV 服务器信息：

```ini:/Volumes/data/pi/arc-export-WebDav/webdav.ini
[webdav]
# WebDAV 服务器 URL (例如: https://dav.jianguoyun.com/dav/)
url = 你的URL

# WebDAV 认证信息
username = 你的邮箱@example.com
password = 你的密码

# 可选设置
# 设置为 true 启用 WebDAV 上传
enabled = true
# WebDAV 服务器上的自定义目录 (留空表示根目录)
directory = bookmark
```

对于坚果云用户：
- URL 使用 `https://dav.jianguoyun.com/dav/`
- 用户名是你的坚果云账号邮箱
- 密码需要使用坚果云的应用密码（在坚果云网页版 -> 账户信息 -> 安全选项 -> 第三方应用管理 中创建）

### 3. 运行脚本

```bash
python3 main.py
```

### 4. 在其他浏览器中设置同步

1. 在 Edge、Chrome、Firefox 等浏览器中安装 [Floccus](https://floccus.org/) 书签同步插件
2. 在 Floccus 中添加 WebDAV 同步账户：
   - 选择 "WebDAV"
   - 输入与 `webdav.ini` 中相同的服务器地址、用户名和密码
   - 指定同步文件夹路径（如：其他收藏夹，不建议和浏览器自己的书签放一起）
3. 设置同步选项（如同步频率等）
4. 点击"立即同步"完成首次同步
注意：坚果云webdav地址后面需带上文件夹名（ini中配置的directory），如https://dav.jianguoyun.com/dav/bookmark/，文件夹需要自己手动创建

## 故障排除

如果遇到问题，可以手动将 `~/Library/Application Support/Arc/StorableSidebar.json` 文件复制到项目目录，然后再次运行脚本。

## 功能特点

- 自动从 Arc 浏览器导出固定标签页
- 转换为标准 HTML 书签格式
- 支持上传到 WebDAV 服务器（如坚果云）
- 通过 Floccus 等插件实现多浏览器间的书签同步

## 致谢

本项目基于 [ivnvxd/arc-export](https://github.com/ivnvxd/arc-export) 开发，感谢原作者的贡献。


## 许可证

本项目遵循 MIT 许可证。