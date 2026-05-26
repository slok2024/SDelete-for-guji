<img width="651" height="917" alt="image" src="https://github.com/user-attachments/assets/57ac83cc-d114-4139-a446-c7d9930927ce" />

🚀 SDeletePro GUI - 数据安全粉碎终端
SDeletePro GUI 是一款基于微软 Sysinternals 核心工具 SDelete 打造的图形化数据销毁终端。它完美结合了底层高强度覆写算法与现代化极简交互，专为对数字化隐私、机密数据销毁有极高要求的用户设计。

无论应对日常的文件防恢复粉碎，还是批量对磁盘未分配空间进行深度清洗填零，本项目都能提供坚实、透明且不可逆的安全保障。

✨ 核心特性

⚡ 独创内核架构自适应检测：
具备智能的系统位数感知能力。通过直接读取 Windows 系统环境变量（而非依赖 Python 内置库的表层判断），即使在 64 位操作系统上运行 32 位的程序环境，也能 100% 精准识别并优先调度 64 位底层安全内核，彻底规避因架构错配引发的底层驱动调用失败。

📥 极简交互 · 鼠标拖拽即粉碎：
完美集成原生 Windows OLE 拖拽事件。支持直接从文件资源管理器中拖放任意数量、任意大小的文件或整个文件夹进入待销毁列表，免去繁琐的路径选择。

📋 智能剪贴板多选导入：
支持在系统文件夹中多选目标并复制（Ctrl+C），回到软件中一键“智能粘贴”，即可自动解析、去重并导入复杂的 Windows 路径组。

⚙️ 核心参数全面控权：
开放微软 SDelete 核心控制链。支持自定义安全覆写轮数（-p）、强制移除只读属性（-r）、递归销毁子目录（-s）以及擦除未分配自由空间（-c）。默认开启静默后台与版权信息屏蔽，净化输出日志。

🛡️ 双重验证与多线程异步安全：
高危操作均配备行业标准的双重确认弹窗。底层执行采用独立的守护线程（Daemon Thread）异步调度，在大文件长时间覆写时界面绝不卡死，回显日志实时可见。

🛠️ 技术栈与架构设计
GUI 容器：Python tkinter (原生轻量，无臃肿依赖)

拖拽引擎：tkinterdnd2 (原生 C 语言动态链接钩子扩展)

核心内核：Microsoft Sysinternals SDelete (通过 subprocess 底层管道安全通信)

并发模型：threading 多线程异步架构 + Tk.after 线程安全 UI 渲染流

📦 编译与打包说明
本项目支持使用 pyinstaller 将 Python 脚本、拖拽引擎元数据以及 32位/64位 微软双内核完美打包成一个独立的单文件 .exe。

1. 安装构建依赖
Bash
pip install tkinterdnd2 pyinstaller
2. 独立单文件全自动化打包命令
将 sdelete32.exe、sdelete64.exe 和 del.py 放置于同一目录下，在终端中运行以下一键命令：

Bash
pyinstaller --noconfirm --onefile --windowed --add-data "sdelete32.exe;." --add-data "sdelete64.exe;." --copy-metadata tkinterdnd2 --name "SDeletePro_Universal" del.py

⚠️ 免责声明 (Disclaimer)
本工具调用的底层 SDelete 覆写行为是完全不可逆的。数据一旦被执行粉碎，任何数据恢复软件（包括低级取证工具）均无法挽回。

请在点击 “启动底层数据销毁” 前，务必反复确认待销毁列表中的路径是否正确。作者及项目贡献者不对任何因误操作导致的数据丢失负责。

📄 开源协议
本项目基于 MIT License 协议开源，欢迎提交 Issue 或 Pull Request 共同完善。
