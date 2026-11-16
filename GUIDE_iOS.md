# 《iPhone / iPad 用户免越狱安装与续签指南》 — MoonLink iOS

> **适用前提**：无需越狱、无需花 $99 购买苹果开发者账号。通过公开的未签名 `.ipa` 安装包与标准软件源，你可以用免费个人 Apple ID 在 iPhone 上免费安装、使用，并实现**无电脑无线自动续签**！

---

## 一、快速选择最适合你的安装路线

| 方案 | 是否需要电脑 | 会不会 7 天过期 | 占用免费 3 个应用名额？ | 推荐指数 |
| --- | --- | --- | --- | --- |
| **1. SideStore（最推荐）** | 仅首次配对用 1 次 | 连上 Wi-Fi 手机端自动无线续签 | 占用 1 个（加 SideStore 共 2 个） | ★★★★★ |
| **2. LiveContainer + SideStore** | 同 SideStore | 同 SideStore 自动续签容器即可 | **不额外占用名额**（容器内可装 N 个 App） | ★★★★★（应用多时首选） |
| **3. 巨魔商店 TrollStore** | 不需要（支持的旧系统） | **永久有效，永不掉签** | **不限数量** | ★★★★★（若系统支持） |
| **4. 轻松签 / Feather / 全能签** | 不需要 | 视个人/企业证书有效期 | 视签名证书 | ★★★★☆ |
| **5. AltStore / Sideloadly / 爱思助手** | 每 7 天需电脑同 Wi-Fi 或插线 | 需电脑刷新（7 天一签） | 占用名额（最多激活 3 个） | ★★★☆☆ |

---

## 二、方案 A：SideStore 软件源一键安装与无线续签（最推荐）

**MoonLink 官方 SideStore / AltStore 软件源链接（复制下面这行）：**

```text
https://raw.githubusercontent.com/YueBao-Idiot/moonlink-ios/main/source.json
```

### 第 1 步：首次在 iPhone 上安装 SideStore（只需这一次借用电脑）
1. 在 iPhone【设置 › 隐私与安全性】最底部开启 **「开发者模式」**（若未显示，将在首次安装侧载应用后出现）。
2. 参考 SideStore 官网文档（[sidestore.io](https://sidestore.io/)）：在 Windows 或 Mac 上使用 `AltServer` + `iTunes/Apple Devices` 将 `SideStore.ipa` 安装到手机，并用 **JitterbugPair** 导出一次 iPhone 配对文件（`.mobiledevicepairing`），发送到手机上导入 SideStore。
3. 在 App Store 搜索并免费下载官方配套本地回环 VPN（例如 **StosVPN**）。

### 第 2 步：在手机上订阅 MoonLink 软件源并安装
1. 在手机打开 **StosVPN** 并开启开关（它只做本地回环转发，不会走外部流量）。
2. 打开 **SideStore**：
   - 点击右下角 **Sources（源）** → 右上角 **+** → 粘贴上方 `source.json` 软件源地址并添加。
   - 刷新源后找到 **MoonLink** → 点击 **GET / Install** 即可直接从软件源下载并签名安装，**完全无需电脑！**
   - 因为 MoonLink 刻意保持“单 Target 极简无特殊权限”，安装和刷新**不会报错**、也不浪费 App ID 配额。

### 第 3 步：彻底告别“7 天掉签”烦恼（自动无线续签）
- 只要连接任意 **Wi-Fi**、打开 **StosVPN**，进入 SideStore 点击 **Refresh All（全部刷新）** 即可将有效期重置为 **7 天**。
- **进阶全自动技巧（苹果快捷指令）**：打开 iPhone 自带「快捷指令 › 自动化」：设置 *每天固定时间或接入 Wi-Fi 时* → 开启 StosVPN → 运行 SideStore 的 *Refresh All Apps* 指令 → 关闭 StosVPN。真正做到零感知永久续签！

---

## 三、方案 B：使用 LiveContainer 突破“免费账号最多装 3 个应用”限制

如果你用免费个人 Apple ID 时，SideStore（1 个）+ 微信/工具已经占满了苹果规定的 **最多同时激活 3 个侧载应用** 与 **每 7 天最多注册 10 个 App ID** 限制，强烈推荐使用 **LiveContainer**！

### 为什么推荐与兼容性评估
- **核心原理**：你只用 SideStore 给 `LiveContainer.ipa` 签名（占用 1 个名额）。之后在 LiveContainer 内部导入 `MoonLink-*-unsigned.ipa`，由容器把 MoonLink 的二进制动态加载执行。
- **关键优势**：
  - **突破 3 应用上限** & **不消耗 App ID**：不管你在 LiveContainer 里装 5 个还是 20 个未签名 App，在苹果系统眼里你永远只安装了一个 LiveContainer！
  - **7 天续签只需续 1 个**：只要 SideStore 续签了 LiveContainer，里面的 MoonLink 就一直不过期。
  - **与 MoonLink 兼容性**：MoonLink 没有使用 Widget / ReplayKit / PushKit 多进程扩展，语音核心完全在主程序 `AudioUnit + UIBackgroundModes=audio` 下运行，已完美契合 LiveContainer 的运行模型！
- **使用注意事项**：
  1. 需从 **LiveContainer 应用内** 点开 MoonLink 启动（或将容器主应用设为 MoonLink 并创建桌面快捷启动方式）。
  2. LiveContainer 与外部安装版本各自有独立的沙盒钥匙串与配置存储，迁移服务器记录和 `.ini` 身份时只需在原客户端 **设置 › 高级 › 导出 .ini** 后在新环境导入即可。

---

## 四、方案 C & D：电脑侧载、巨魔商店与自签名证书安装

从公开 Release 页面下载最新包：`https://github.com/YueBao-Idiot/moonlink-ios/releases`

1. **巨魔商店（TrollStore）**：
   - 如果你的 iPhone/iPad 系统停留在巨魔支持范围（如 iOS 14.0 – 16.6.1 / 17.0 部分环境），直接用 Safari 下载 `MoonLink-*-unsigned.ipa`，分享打开到 **TrollStore** 安装，**永久免签名、永不过期、不限数量**！
2. **Sideloadly / 爱思助手 / AltStore Classic**：
   - **Sideloadly**（Win/Mac）：数据线连手机，拖入 `.ipa`，填入免费 Apple ID 即可签装（注意不要修改 Bundle ID 后附加多扩展）。
   - **爱思助手**（仅需免费签名）：工具箱 → IPA 签名 → 添加 Apple ID 自签后安装。
3. **轻松签（ESign）/ Feather / 全能签**：
   - 若你购有个人 P12 证书或使用兼容签名工具，直接导入 `.ipa` 并用你的 `.p12 + .mobileprovision` 签名安装即可（无需调整权限）。

---

## 五、iPhone 端关键功能与系统限制说明

### 1. 息屏与后台持续语音保活
- MoonLink 使用了苹果允许免费签名开启的 `UIBackgroundModes = audio` 后台音频通道，配合静音零电平输出保活机制：进入频道后**无论你是否静音麦克风，锁屏息屏或切到微信/游戏后台，TeamSpeak 的 UDP 心跳和好友语音都会持续稳定在线**，不会动不动掉线触发“克隆号冲突 (521)”。
- 当你手动关闭麦克风时，MoonLink 会智能关闭硬件采集总线、保留仅输出心跳状态，因此**屏幕右上角橙色麦克风状态点会自动消失**，兼顾隐私与续航！

### 2. 蓝牙耳机音质发闷 & 独立选择麦克风（实话实说系统限制）
- **苹果 iOS 系统机制**：当应用启用麦克风录音时，如果选择蓝牙耳机麦克风（AirPods 等），iOS 会强制把整条蓝牙链路切换为通话协议 **HFP（8 kHz / 16 kHz 单声道低码率）**，导致耳机听歌/语音发闷。
- **MoonLink 独家解法**：
  - 在 **设置 › 采集 › 采集设备** 中选择 **「内置麦克风」**！
  - MoonLink 会自动禁用蓝牙 HFP 通话通道、只允许高音质 **A2DP 立体声** 传输给耳机播放声音，同时强制用 **iPhone 机身内置麦克风** 拾取你的人声。
  - 若你在佩戴蓝牙耳机/有线耳机时感觉人声断续或被吃掉末尾声音，建议在 **设置 › 采集 › 信号处理** 中**关闭「回声消除 (VoiceProcessingIO)」**，改为开启 **「AI 降噪 (RNNoise)」**，你会立刻获得像桌面端一样通透清晰的音质！
- 若你需要把声音从“扬声器”切换到指定的 AirPods / HomePod / AirPlay 设备，可在 **设置 › 播放** 点击 **「系统音频输出路由」** 图标直接调用系统原生面板选择。
