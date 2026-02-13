# Windows 7 更新合集

## 简介
Windows 7 在 2020 年 1 月结束支持，此后可以获得 3 年的扩展安全更新 (ESU) ，直到 2023 年 1 月。但是，64 位 Windows 7 可以安装 Windows Server 2008 R2 的 ESU 更新直到 2026 年 1 月，32 位 Windows 7 可以安装 Windows Embedded Standard 7 的 ESU 更新直到 2024 年 10 月。

所有的 ESU 更新现已结束，所以我整理了 Windows 7 的更新合集。

这套合集适用于非英语版本的 Windows 7 SP1 全新安装 (2011 年原版光盘映像)。微软在 2019 年发布过英语版 Windows 7 的新版光盘映像，所以英语版不需要我这套合集里的许多更新。英语版本的 Windows 7 更新指南：https://hackandpwn.com/windows-7-esu-patching/

我想过把更新离线集成到系统映像中，但是部分更新是不能使用 DISM 离线集成的，必须在线安装才能正确生效。而且第三方提供的系统映像不能被轻易信任。所以我选择了更新合集的方式，这里面每个更新都有微软的数字签名。

这套更新合集包含了 Internet Explorer 11 (简体中文)、最新的 ESU 月度安全质量汇总、便利性汇总更新 (KB3125574，俗称 SP2)，以及让 Windows Update 满意的其他更新的最小子集。此外，还包含了以下更新：

- 13个可选功能更新：
  - Active Directory Lightweight Directory Services
  - DirectAccess Connectivity Assistant 2.0
  - Embedded Lockdown Manager
  - File Management API Update
  - Microsoft Agent
  - NTBackup
  - Remote Server Administration Tools
  - Windows Help
  - Windows Identity Foundation
  - Windows Media Services Remote Server Administration Tools
  - Windows Server Essentials Connector
  - Windows Virtual PC
  - Work Folders

  其中，NTBackup 只有在显示语言是英语时才可以安装，所以我还提供了英语语言包。
  
- KB3191566：Windows Management Framework 5.1
- KB2990999：Internet Explorer 11 Web Driver Tool
- KB2818604：AMD Microcode Update
- KB3046480：.NET Framework 1.1 Migration Check
- KB3064209：Intel Microcode Update
- KB4072650：Hyper-V Integration Components Update
- KB4578847：Update for Application and Device Compatibility

另外，我还整理了适用于 Windows 7 的软件合集，包含：
- DirectX 9.0c End-User Runtime
- Microsoft Camera Codec Pack
- Microsoft Edge v109 (最后支持 Windows 7 的版本)
- Microsoft Security Essentials
- Microsoft YaHei UI (从 Windows 11 拿来的，安装字体后可解决 IE11 字体异常)
- Pinyin (包含必应输入法、谷歌拼音输入法)
- PowerShell v7.2.24 (最后支持 Windows 7 的版本)
- Visual C++ Redistributable
- Windows Journal (简体中文)
- Windows Live Essentials 2012 (简体中文)
- Windows XP Mode

## 安装指导
在安装更新期间，建议把 Windows Update 设为「从不检查更新」。

必须按照以下顺序进行安装：

1. 00_SSU-201903：以管理员身份运行 Update.cmd，安装 2019 年 3 月 服务堆栈更新。
2. 01_Optional-Features：根据需要选择安装可选功能更新。注意：安装 AD LDS (KB975541) 后必须安装随附的 6 个更新，因为 SP2 不能正确地更新 AD LDS。详细分析见：http://windows-update-checker.com/FAQ/ConvenienceRollupKB3125574-Issues.htm
3. 02_Updates1：以管理员身份运行 Update.cmd，安装第 1 组更新。
4. 03_Updates2：以管理员身份运行 Update.cmd，安装第 2 组更新。
5. 04_Remove-Old：以管理员身份运行 Remove_OLD.cmd，卸载 KB2534111 和 IE8。
   
在进行以下步骤之前，请确保设备已获得有效的 ESU 许可。

6. 05_Updates3：以管理员身份运行 Update.cmd，安装第 3 组更新。
7. 06_Convenience-Rollup：以管理员身份运行 Update.cmd，安装便利性汇总更新。
8. 07_NDP48：安装 .Net Framework 4.8。
9. 08_WMF51：以管理员身份运行 Update.cmd，安装 Windows Management Framework 5.1。
10. 安装你喜欢的软件更新。提示：如果 Microsoft Security Essential 无法更新定义，可以运行 MicrosoftEasyFix51044 来解决。

安装完更新合集后，Windows Update 可能会检查出以下更新：

- KB4493132/KB4524752：Windows 7 停止支持通知
- KB5001027：Microsoft Edge
- KB890830：恶意软件删除工具
- KB915597：Windows Defender 定义更新

感谢：[KUC Windows Update Checker](http://www.windows-update-checker.com/)
