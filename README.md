# 流萤加速器 (FireflyVPN)

<p align="center">
  <img src="./images/firefly.jpg" width="100" alt="Logo">
</p>
<p align="center">
  <img src="https://img.shields.io/badge/Platform-Android-brightgreen" alt="Platform">
  <img src="https://img.shields.io/badge/Min%20SDK-24%20(Android%207.0)-blue" alt="Min SDK">
  <img src="https://img.shields.io/badge/Target%20SDK-35%20(Android%2015)-blue" alt="Target SDK">
  <img src="https://img.shields.io/badge/Language-Kotlin-purple" alt="Language">
  <img src="https://img.shields.io/badge/Core-Sing--box-green" alt="Core">
  <img src="https://img.shields.io/badge/License-GPLv3-orange" alt="License">
</p>
<p align="center">
  流萤加速器是一款基于 sing-box 核心，支持多种代理协议和智能分流的 Android VPN 客户端。
</p>

<p align="center">
  <a href="#功能特性">功能特性</a> •
  <a href="#技术架构">技术架构</a> •
  <a href="#环境要求">环境要求</a> •
  <a href="#快速开始">快速开始</a> •
  <a href="#配置说明">配置说明</a> •
  <a href="#API 接口">API 接口</a> •
  <a href="#自定义">自定义</a> •
  <a href="#构建发布">构建发布</a> •
  <a href="#其他说明">其他说明</a>
</p>

---

**免责声明：** 本项目为本人开源作品，与米哈游 (HoYoverse) 无关。本项目不盈利、不接受捐赠。所有涉及的游戏角色名称及设计版权归米哈游所有。

**Disclaimers:** This project is my open-source creation and is not related to miHoYo (HoYoverse). This project is non-profit and not for sale. All game character names and design copyrights belong to miHoYo.

---

## 界面展示

---

<div style="display:flex;gap:16px;flex-wrap:wrap;max-width:100%;"><img style="width:360px;max-width:100%;height:auto;border-radius:10px;box-shadow:0 4px 12px rgba(0,0,0,.08);" src="./images/1.jpg" alt="image1"/><img style="width:360px;max-width:100%;height:auto;border-radius:10px;box-shadow:0 4px 12px rgba(0,0,0,.08);" src="./images/2.jpg" alt="image2"/><img style="width:360px;max-width:100%;height:auto;border-radius:10px;box-shadow:0 4px 12px rgba(0,0,0,.08);" src="./images/3.jpg" alt="image3"/><img style="width:360px;max-width:100%;height:auto;border-radius:10px;box-shadow:0 4px 12px rgba(0,0,0,.08);" src="./images/4.jpg" alt="image4"/></div>

---

## 功能特性

### 核心功能

- 🚀 **多协议支持**：VLESS、VMess、Trojan、Hysteria2、AnyTLS、TUIC、Naive、WireGuard、Shadowsocks、SOCKS4/5、HTTP/HTTPS 代理
- 🧭 **智能分流**：国内流量直连，国外流量代理，自动识别主流 CN 应用/CDN
- ⚡ **自动选择**：一键测速，自动选择最优节点
- 📦 **分应用代理**：精细控制哪些应用走代理或绕过 VPN
- 🌐 **绕过局域网**：一键开关，局域网流量直连不受影响
- 🖥️ **局域网代理**：开启 VPN 后提供 HTTP / SOCKS5 局域网代理端口，电脑、平板等同网设备可通过手机当前节点访问网络
- 🌍 **IPv6 路由**：支持 IPv6 网络访问，可选禁用/启用/优先/仅 IPv6 模式
- 🔄 **备用节点**：支持配置备用订阅源，主节点不可用时可快速切换
- ⭐ **收藏节点**：收藏节点与主/备用订阅节点独立存储，订阅刷新不会覆盖收藏内容
- ➕ **节点导入**：节点列表支持从剪切板导入和扫码导入，导入结果自动去重并写入收藏节点
- 🛡️ **核心配置校验**：收藏导入与 VPN 启动前会使用 sing-box `checkConfig` 校验节点配置，避免单个不兼容节点拖垮整组配置

### 测试与诊断

- 🔧 **三点工具菜单**：主界面右上角“三点”菜单提供 TCPing、URL Test、网速测试、流媒体解锁测试、节点IP信息、隐藏超时/不可用节点、网络工具箱等功能
- 🌐 **URL Test 测试**：通过启动临时无头 sing-box 实例进行 HTTP 握手延迟测试，无需连接 VPN 即可测试所有节点真实连通性
- 🧠 **择优面板（全屏横屏）**：升级版自动化测试入口，支持横屏沉浸式配置、更多参数同屏展示、模式化测试与一键择优
- 🧩 **测试模式系统**：内置 `日常模式`（URL Test 延迟优先）与 `下载模式`（下行带宽优先，默认 10MB），支持自定义模式保存/删除
- 🤖 **自动化测试流程**：支持配置后自动执行“拉节点 → 延迟测试 → 延迟筛选 → 带宽测试 → 带宽筛选 → 解锁测试”，并弹出结果总览与节点详情
- 🎯 **智能择优规则**：支持延迟优先 / 上行优先 / 下行优先 / 解锁情况优先（解锁数或指定网站多选优先）
- 🎬 **流媒体解锁测试**：集成 UnlockTests，可逐节点测试国外主流网站解锁情况并展示可滚动结果明细，支持“当前节点”一键勾选与“随机测试节点数”勾选
- ⚡ **Cloudflare 网速测试**：集成 Cloudflare Speed Test，支持下载/上传测速，实时显示速率
- 📡 **TCPing 测试**：直接 TCP 连接测试节点可达性和延迟
- 🔍 **节点出口 IP 信息查询**：在三点菜单中可基于“当前选择节点”查询出口 IP 详细信息（地区、ASN、欺诈评分、是否住宅/原生IP等），无需先连接主 VPN（通过临时本地 SOCKS 代理走所选节点出口发起查询）
- 🗑️ **清理不合格节点**：一键隐藏超时/不可用/不达标节点（UI 过滤，不删除数据库数据）
- 📂 **按节点来源测试**：TCPing、URL Test、流媒体测试、网速测试和择优面板会按当前选择的主/备用节点或收藏节点执行
- 🧾 **运行日志**：侧边栏可查看、刷新、分享、清空 APP 内部运行日志；日志仅记录脱敏后的关键 Info / Warn / Error，不导出节点链接和配置内容
- 🛠️ **网络工具箱**：内置 10 种常用网络检测工具（出口检测、IP查询、WebRTC泄漏、DNS泄漏、速度测试等），一键跳转浏览器使用

### 界面与体验

- 🚩 **智能国旗**：自动识别节点名称中的国旗 Emoji（如 🇫🇮），优雅展示
- 🔔 **VPN 通知**：实时显示上传/下载速度、累计流量，支持断开/重置连接
- ⏳ **节流保护**：刷新、切换备用节点、检查更新等操作 5 秒内防重复触发
- 🔔 **公告系统**：支持远程推送公告通知
- ℹ️ **关于页面**：展示应用版本信息、开源协议、GitHub 仓库链接和免责声明
- ⚙️ **其他配置**：侧边栏可进入“其他配置”页面，集中管理 IPv6 路由、绕过局域网、夜间模式、自动执行、超时时间、并发数、VPN MTU 等参数
- 🔋 **后台稳定性提示**：局域网代理页面支持检测/管理“忽略电池优化”，提升长时间代理稳定性
- 🚀 **启动画面**：可配置启动倒计时时长（支持跳过），可在 `AppConfig.kt` 中设置 `STARTUP_SPLASH_DURATION_SECONDS`
- 🌙 **夜间模式**：其他配置中可选择跟随系统、浅色或深色主题
- 💾 **记住上次选择节点**：默认开启，退出 APP 前选择的节点会在下次启动后恢复
- 🎨 **现代 UI**：基于 Jetpack Compose，Material Design 3 风格，页面使用 NavHost + NavController 路由管理
- 🔧 **开源可定制**：易于修改 API、品牌和配置

### 更新与安全

- 📦 **稳健更新**：
  - 应用内下载，支持断点续传
  - 自动检测下载失败，连续失败 3 次及以上会引导跳转官网下载
  - 原子化更新机制，杜绝安装包损坏
  - 智能权限引导，适配 Android 8.0+ 安装权限

---

## 技术架构

| 组件 | 技术 |
|------|------|
| **UI 框架** | Jetpack Compose + Material 3 |
| **页面路由** | NavHost + NavController (Jetpack Navigation Compose) |
| **架构模式** | MVVM (ViewModel + StateFlow) |
| **网络请求** | Retrofit2 + OkHttp3 |
| **本地存储** | Room Database (SQLCipher 加密) + DataStore |
| **二维码扫描** | CameraX + ML Kit Barcode Scanning |
| **运行日志** | 应用内专用 RuntimeLog（私有文件 + FileProvider 分享） |
| **VPN 核心** | [sing-box](https://github.com/SagerNet/sing-box) (libbox.aar) |
| **并发处理** | Kotlin Coroutines |

---

## 环境要求

### 开发环境

| 工具 | 版本要求 |
|------|---------| 
| **Android Studio** | Koala 2024.1.1 或更高 |
| **JDK** | 17 |
| **Kotlin** | 1.9.21 |
| **Gradle** | 8.7+ |
| **Android Gradle Plugin** | 8.6.1 |
| **NDK** | 25.1.8937393 |

### 运行环境

| 要求 | 说明 |
|------|------|
| **Android 版本** | Android 7.0 (API 24) 及以上 |
| **目标版本** | Android 15 (API 35) |

### 核心依赖

项目依赖 `libbox.aar`（sing-box Android 库），需放置于 `app/libs/` 目录。

项目还包含 [UnlockTests](https://github.com/oneclickvirt/UnlockTests) Android so库（用于流媒体解锁测试）：

这两个so库是由`ut-android-arm64`和`ut-android-armv7`两个二进制文件（[UnlockTests](https://github.com/oneclickvirt/UnlockTests) 项目编译得到，建议放到`app/src/main/assest/bin`目录下）复制到 jniLibs 对应 ABI 目录，然后挂到 preBuild，最后 build 自动迁移生成的！

- `app/src/main/jniLibs/arm64-v8a/libut.so`
- `app/src/main/jniLibs/armeabi-v7a/libut.so`

> **获取 libbox.aar**：
>
> - 从 [sing-box Releases](https://github.com/SagerNet/sing-box/releases) 下载预编译版本
> - 或参考 [libbox 构建指南](https://sing-box.sagernet.org/installation/build-from-source/#build-libbox-for-android) 自行编译

项目还依赖 [SQLCipher for Android](https://github.com/niceyun/sqlcipher-android)（`net.zetetic:sqlcipher-android:4.13.0`）用于本地数据库加密，Gradle 会自动下载，无需手动配置。

---

## 快速开始

### 1. 克隆项目

```bash
git clone https://github.com/Iskongkongyo/FireflyVPN.git
cd FireflyVPN
```

### 2. 配置 libbox

将 `libbox.aar` 文件放入 `app/libs/` 目录：

```
app/
└── libs/
    └── libbox.aar
```

### 3. 配置 API 地址

编辑 `app/src/main/java/xyz/a202132/app/AppConfig.kt`，修改为你的后端地址：

```kotlin
object AppConfig {
    const val STARTUP_SPLASH_DURATION_SECONDS = 10 // 启动图倒计时时长，设为0则不启用

    // 节点订阅 API
    const val SUBSCRIPTION_URL = "https://your-server.com/api/nodes"
    // 版本更新 API
    const val UPDATE_URL = "https://your-server.com/api/update" // 留空则不检查更新且隐藏入口
    // 公告通知 API
    const val NOTICE_URL = "https://your-server.com/api/notice"
    // 官网地址
    const val WEBSITE_URL = "https://your-server.com" // 留空则隐藏“官方网站”

    // API 请求超时（毫秒）
    const val NODE_REQUEST_TIMEOUT_MS = 25000L    // 节点请求超时
    const val NOTICE_REQUEST_TIMEOUT_MS = 25000L  // 公告请求超时
    const val UPDATE_REQUEST_TIMEOUT_MS = 25000L  // 更新请求超时

    // 联系方式
    const val FEEDBACK_EMAIL = ""  // 反馈邮箱，留空则不显示邮箱复制
    // 反馈链接（GitHub Issues）
    const val FEEDBACK_URL = "https://github.com/your-username/your-repo/issues" // 与邮箱均留空则隐藏“问题反馈”
    // 项目源码地址（留空则隐藏关于页相关按钮）
    const val GITHUB_URL = "https://github.com/your-username/your-repo"

    // 延迟测试 (TCPing & URL Test)
    const val TCPING_TEST_TIMEOUT = 3000L // 超时默认3秒
    const val URL_TEST_URL = "https://www.google.com/generate_204"
    const val URL_TEST_TIMEOUT = 3000L // 超时默认3秒
    const val URL_TEST_RETRY_COUNT = 1 // URL Test 自动重试次数，仅对503/504或异常生效
    
    // 延迟测试并发数
    const val TCPING_CONCURRENCY = 16
    const val URL_TEST_CONCURRENCY = 10
    const val AUTO_TEST_UNLOCK_CONCURRENCY = 3 // 流媒体解锁测试并发建议2~3

    // VPN 核心参数
    const val VPN_MTU = 9000
    const val VPN_DNS_PRIMARY = "8.8.8.8"
    const val VPN_DNS_SECONDARY = "8.8.4.4"
    const val VPN_DNS_CHINA = "223.5.5.5"        // 国内 DNS（智能分流模式使用）
    val HTTP_USER_AGENT: String  // 运行时 getter，自动跟随版本号
        get() = "FireflyVPN/${BuildConfig.VERSION_NAME}"

    // 通知
    const val NOTIFICATION_CHANNEL_ID = "vpn_service"
    const val NOTIFICATION_ID = 1

    // 节点出口 IP 信息查询
    const val NODE_IP_INFO_URL = "https://my.ippure.com/v1/info"
    const val NODE_IP_INFO_TIMEOUT_MS = 12000L
    const val NODE_IP_INFO_RETRY_COUNT = 1 // 节点IP信息自动重试次数

    // 速度测试 (Cloudflare)
    const val SPEED_TEST_DOWNLOAD_URL = "https://speed.cloudflare.com/__down"
    const val SPEED_TEST_UPLOAD_URL = "https://speed.cloudflare.com/__up"
    const val AUTO_TEST_BANDWIDTH_DOWNLOAD_TIMEOUT_MS = 25000L // 单次下载带宽测试超时
    const val AUTO_TEST_BANDWIDTH_UPLOAD_TIMEOUT_MS = 30000L   // 单次上传带宽测试超时
}
```

同时修改 `app/src/main/java/xyz/a202132/app/network/NetworkClient.kt` 中的 baseUrl：

```kotlin
private val retrofit = Retrofit.Builder()
    .baseUrl("https://your-server.com/")  // 修改为你的域名
    // ...
```

同时修改 `app/src/main/res/xml/network_security_config.xml` ：

```xml
<domain includeSubdomains="true">example.com</domain> <!-- 修改为你的域名 -->
```

### 4. 构建运行

```bash
# 使用 Gradle 构建
./gradlew assembleDebug

# 或在 Android Studio 中直接运行
```

---

## 配置说明

### 项目结构

```
app/src/main/java/xyz/a202132/app/
├── AppConfig.kt                  # 全局配置常量（API地址、网络工具箱等）
├── MainActivity.kt               # 主 Activity
├── VpnApplication.kt             # Application 类
├── data/
│   ├── local/                    # 本地数据库
│   │   ├── AppDatabase.kt       # Room 数据库定义
│   │   └── NodeDao.kt           # 节点数据访问对象
│   ├── model/                    # 数据模型
│   │   ├── AppThemeMode.kt       # APP 显示主题模式枚举
│   │   ├── ApiModels.kt         # API 响应模型
│   │   ├── Node.kt              # 节点数据模型
│   │   ├── NodeType.kt          # 代理协议类型枚举
│   │   ├── PerAppProxyMode.kt   # 分应用代理模式枚举
│   │   └── IPv6RoutingMode.kt   # IPv6 路由模式枚举
│   └── repository/               # 数据仓库
│       └── SettingsRepository.kt # 设置存储（含分应用代理、绕过局域网等）
├── network/
│   ├── ApiService.kt             # Retrofit API 接口定义
│   ├── DownloadManager.kt        # 应用内下载管理器（断点续传）
│   ├── LatencyTester.kt          # 节点延迟测试（TCPing + URL Test）
│   ├── NetworkClient.kt          # 网络客户端配置
│   ├── SpeedTestService.kt       # Cloudflare 网速测试服务
│   ├── SubscriptionParser.kt     # 订阅链接解析器
│   ├── UnlockTestManager.kt      # 流媒体解锁测试临时代理管理器
│   └── UrlTestManager.kt         # 无头 sing-box URL Test 管理器
├── service/
│   ├── BoxPlatformInterface.kt   # sing-box 平台接口（TUN 管理、分应用代理）
│   ├── BoxVpnService.kt          # VPN 服务（sing-box 核心）
│   ├── HeadlessPlatformInterface.kt  # 无头平台接口（URL Test 专用）
│   └── ServiceManager.kt         # VPN 服务管理器
├── ui/
│   ├── components/               # 可复用 UI 组件
│   │   ├── AppScreenScaffold.kt # 通用页面脚手架（统一 TopAppBar + 返回键）
│   │   ├── ConnectButton.kt     # 连接按钮
│   │   ├── DrawerContent.kt     # 侧边栏内容
│   │   ├── TestPreferPanelDialog.kt # 择优面板（全屏横屏）
│   │   ├── NodeListDialog.kt    # 节点列表页面（文件名沿用旧命名，主入口已改为 NodeListScreen）
│   │   ├── NodeSelector.kt      # 节点选择器
│   │   ├── StartupSplashOverlay.kt  # 启动画面覆盖层（可配置倒计时）
│   │   └── TrafficStatsRow.kt   # 流量统计展示
│   ├── dialogs/                  # 对话框
│   │   ├── AboutDialog.kt       # 关于页面弹窗
│   │   ├── AutoTestResultDialog.kt  # 自动化测试结果与详情弹窗
│   │   ├── Dialogs.kt           # 通用对话框（公告、更新等）
│   │   ├── NetworkToolboxDialog.kt  # 网络工具箱页面（文件名沿用旧命名，主入口已改为 NetworkToolboxScreen）
│   │   ├── NodeIpInfoDialog.kt      # 节点出口 IP 信息弹窗
│   │   ├── SpeedTestDialog.kt       # 网速测试弹窗
│   │   ├── UnlockTestDialog.kt      # 流媒体解锁测试弹窗（旧入口，新入口见 UnlockTestScreen）
│   │   └── UserAgreementDialog.kt   # 用户协议弹窗
│   ├── navigation/               # 页面路由
│   │   └── AppRoute.kt          # 路由常量定义（NavHost 目的地）
│   ├── screens/                  # 页面（通过 NavHost + NavController 管理）
│   │   ├── MainScreen.kt        # 主界面
│   │   ├── LanProxyScreen.kt    # 局域网代理设置页面
│   │   ├── RuntimeLogScreen.kt  # 运行日志页面
│   │   ├── OtherConfigScreen.kt # 其他配置页面（网络/主题/自动执行/超时/并发/MTU）
│   │   ├── PerAppProxyScreen.kt # 分应用代理设置界面
│   │   ├── QrScannerScreen.kt   # 二维码扫描导入页面
│   │   └── UnlockTestScreen.kt  # 流媒体解锁测试页面
│   └── theme/                    # 主题配置
│       ├── Color.kt             # 颜色定义
│       ├── Theme.kt             # 主题配置
│       └── Type.kt              # 字体排版
├── util/
│   ├── CryptoUtils.kt           # AES 加解密工具
│   ├── DatabasePassphraseManager.kt # SQLCipher 数据库密钥管理（Android Keystore）
│   ├── NetworkUtils.kt          # 网络状态检测工具
│   ├── RuleManager.kt           # 智能分流规则管理
│   ├── RuntimeLog.kt            # 应用内运行日志（脱敏、滚动保留、导出）
│   ├── SignatureVerifier.kt     # APK 签名验证（JNI 桥接）
│   ├── SingBoxConfigGenerator.kt # sing-box 配置生成器
│   └── UnlockTestsRunner.kt      # UnlockTests 二进制执行器
└── viewmodel/
    ├── AutoTestState.kt          # 自动化测试状态模型
    ├── GlobalTestExecution.kt    # 全局测试互斥锁
    ├── MainViewModel.kt          # 主界面 ViewModel
    ├── PerAppProxyViewModel.kt   # 分应用代理 ViewModel
    └── UnlockTestViewModel.kt    # 流媒体解锁测试 ViewModel
```

### 资源文件结构

```
app/libs/libbox.aar               # sing-box 核心库
app/src/main/
├── assets/
│   └── rule-sets/                # 智能分流规则集
│       ├── geoip-cn.srs
│       └── geosite-cn.srs
├── cpp/
│   ├── CMakeLists.txt            # NDK 构建配置
│   └── native-lib.cpp            # Native 层（AES 密钥 + 签名校验）
├── jniLibs/
│   ├── arm64-v8a/libut.so        # UnlockTests (ARM64)
│   └── armeabi-v7a/libut.so      # UnlockTests (ARMv7)
├── res/
│   ├── drawable/                 # 图标和图片资源
│   ├── mipmap-*/                 # 应用图标
│   ├── values/
│   │   ├── colors.xml            # 颜色资源
│   │   ├── strings.xml           # 字符串资源
│   │   └── themes.xml            # 主题定义
│   └── xml/
│       ├── file_paths.xml        # FileProvider 路径配置
│       └── network_security_config.xml  # 网络安全配置
└── AndroidManifest.xml           # 应用清单
```

---

## 高级功能

### 节点列表、收藏与导入

节点列表支持在 `主节点/备用节点` 与 `收藏节点` 两个视图之间切换。收藏节点是独立数据，不会在主/备用订阅刷新后被自动覆盖。

**功能特点**：

- ⭐ 节点卡片延迟标签前的星标可用于收藏或取消收藏
- 📌 APP 会记录退出前停留的是主/备用节点还是收藏节点
- ➕ 节点列表搜索按钮左侧提供导入入口，支持从剪切板导入和扫描二维码
- 🔁 导入到收藏节点前会自动去重，成功后提示实际导入数量
- 🛡️ 导入收藏节点前会生成单节点 sing-box 测试配置并执行 `Libbox.checkConfig()`，不兼容核心的节点不会写入收藏
- 🚦 VPN 启动时只会使用当前节点来源生成配置，并在启动前跳过核心不支持的非选中节点；如果所选节点本身不被核心支持，会直接提示错误

> 💡 收藏节点适合长期保留少量手动维护的节点；主/备用节点适合由订阅接口统一刷新。

---

### 工具箱按钮

主界面右上角“三点”菜单提供以下功能：

| 功能 | 说明 |
|------|------|
| **TCPing** | 直接 TCP 连接测试节点可达性和延迟 |
| **URL Test** | 通过 ClashAPI 发起 HTTP 握手延迟测试，结果更准确 (默认/推荐) |
| **网速测试** | 使用 Cloudflare 节点进行真实宽带测速 |
| **隐藏不合格节点** | 一键隐藏超时/不可用/不达标节点（UI 过滤） |
| **流媒体解锁测试** | 调用 UnlockTests 逐节点测试解锁能力，支持“当前节点”一键勾选与随机节点数勾选 |
| **节点 IP 信息** | 查询当前选择节点的出口 IP 详情（地区、ASN、风控评分等，选中即可，无需连接） |
| **网络工具箱** | 打开内置网络工具站点集合 |

**URL Test 工作原理**：

- **VPN 已连接时**：直接使用现有 sing-box 实例的 ClashAPI (端口 9090)
- **VPN 未连接时**：自动启动临时无头 sing-box 实例 (端口 19090)，无需 VPN 权限即可测试

> 💡 无头实例不使用 TUN，仅创建本地 HTTP 代理和 ClashAPI，通过操作系统默认路由直接连接代理节点。

---

### 网络工具箱

内置 10 种常用网络检测工具，可在 `AppConfig.kt` 的 `NETWORK_TOOLS_JSON` 中自定义配置：

| 工具 | 用途 | 网站 |
|------|------|------|
| 出口检测 | 检测 VPN 出口 IP | ippure.com |
| IP信息查询 | 查询 IP 详细信息 | ippure.com |
| WebRTC泄漏 | 检测 WebRTC 是否泄漏真实 IP | ippure.com |
| DNS泄漏 | 检测 DNS 请求是否走代理 | ippure.com |
| IP检测 | 综合 IP 检测 | ipcheck.ing |
| 高精度IP查询 | 高精度 IP 地理位置 | ping0.cc |
| IP定位 | IP 地理定位 | iplark.com |
| 伪装度查询 | 代理伪装度检测 | whoer.net |
| BGP查询 | BGP 路由信息 | bgp.tools |
| 速度测试 | 网络速度测试 | speedtest.net |

**自定义工具列表**：

修改 `AppConfig.kt` 中的 JSON 数组即可添加、删除或修改工具项：

```kotlin
const val NETWORK_TOOLS_JSON = """
[
  {"name": "工具名称", "url": "https://example.com", "icon": "speed"}
]
"""
```

支持的图标标识：`outbound`、`ip`、`webrtc`、`dns`、`check`、`precision`、`location`、`disguise`、`bgp`、`speed`

---

### 择优面板（兼容自动化测试） 🚀

“择优面板”是在原自动化测试基础上的增强入口，适合需要频繁调整筛选条件、快速换策略的场景。面板为**全屏横屏沉浸式**，参数更多、视野更大，调起来更顺手 ✨

**核心能力**：

- 🧩 **测试模式**：支持保存/删除当前面板配置，内置 `日常模式`、`下载模式`
- 🎛️ **模式化执行**：首页中间按钮可先选模式，再执行测试并自动连接最优节点
- 🔄 **启动自动执行**：开启后会执行“当前模式”测试（并 Toast 提示当前模式名）
- 🗑️ **移除未达标**：快速隐藏不可用/超时/筛选失败节点（UI 过滤）
- 🎯 **自动连接最优**：按当前模式的默认择优规则一键连接

**自动化测试链路（按启用项执行）**：

1. 拉取节点
2. 延迟测试（可选TCPing或URL Test）
3. 按延迟阈值筛选（可选）
4. 逐节点带宽测试（下载/上传，支持下载测试流量大小 1/10/25/50MB）
5. 按带宽阈值筛选（可选）
6. 逐节点流媒体解锁测试（UnlockTests，可选）
7. 弹出“自动化测试结果”弹窗（支持关键词搜索、节点详情、自动连接最优、手动选择节点连接）

**择优规则（模式默认规则 + 手动选择）**：

- `延迟优先`：延迟越低越优（仅在当前模式启用了延迟测试且已有对应结果时生效）
- `上行优先`：上传越高越优（仅在启用了上传测速且有结果时生效）
- `下行优先`：下载越高越优（仅在启用了下载测速且有结果时生效）
- `解锁情况优先`：支持两种子策略（仅在启用了解锁测试且有结果时生效）
  - `按解锁数`：按总解锁数量排序
  - `按指定网站（多选）`：按目标网站命中数优先，适合只关心少数站点的场景

> 💡 当你只“保存了规则”但还没做对应测试时，APP 会提示先测试，不会拿无关历史数据“乱选节点”。

**解锁优先（按指定网站）预设站点**

预设站点来自 UnlockTests 实测输出整理（如 `ChatGPT`、`Claude`、`Gemini`、`Netflix`、`Disney+`、`TikTok`、`YouTube Region`、`Amazon Prime Video`、`MetaAI`、`SonyLiv` 等），统一维护在 `AppConfig.kt` 的 `UNLOCK_PRIORITY_PRESET_SITES` 中，方便后续扩展。

**入口位置**：

- 侧边栏 → `择优面板`
- 首页中间按钮（弹模式选择后执行）

---

### 关于页面

显示应用版本信息、开源协议声明、项目链接等。

**配置位置**：  
- 版本号：`app/build.gradle.kts` → `versionName` / `versionCode`  
- GitHub 链接：`AppConfig.kt` → `GITHUB_URL`（留空则隐藏相关按钮）  
- 反馈链接：`AppConfig.kt` → `FEEDBACK_URL`

**设置位置**：侧边栏 → 关于

---

### 分应用代理

分应用代理允许用户精细控制哪些应用走代理或绕过 VPN。

**功能特点**：
- 🟢 **代理模式**：只有选中的应用走代理，其他应用直连
- 🔴 **绕过模式**：选中的应用直连，其他应用走代理
- 🔍 **搜索过滤**：支持按应用名称或包名搜索
- 📂 **系统应用筛选**：可选择显示/隐藏系统应用

**设置位置**：侧边栏 → 分应用代理

---

### 其他配置

"其他配置"页面集中管理网络开关、显示主题、自动执行、测试超时、并发数和 VPN 参数。顶部网络区（IPv6 路由、绕过局域网）点击后立即生效；其余输入型参数修改后点击"保存"生效。

| 配置项 | 默认值 | 说明 |
|--------|--------|------|
| IPv6 路由 | 禁用 | 可选仅 / 优先 / 启用 / 禁用，位于其他配置顶部 |
| 绕过局域网 | 开启 | 局域网流量直连，位于其他配置顶部 |
| 夜间模式 | 跟随系统 | 可选跟随系统 / 浅色 / 深色 |
| APP启动默认测试 | 不执行 | 可选不执行 / TCPing / URL Test |
| 记住上次选择的节点 | 开启 | 退出 APP 前选择的节点会在下次启动后恢复 |
| VPN连接后获取IP信息 | 关闭 | 仅影响后续新的连接动作 |
| 定时更新节点信息 | 关闭 | 可设置每隔 X 小时 Y 分钟自动请求节点；从上次请求节点完成后开始计时，并沿用上次使用的主/备用节点来源 |
| 节点自动重连 | 关闭 | 定时更新后，如当前连接节点的 `server + port` 仍存在，则自动重连到新列表中的对应节点；不存在则保持原连接 |
| 节点更新通知 | 开启 | 仅控制定时更新节点信息产生的 Toast 提示，不影响手动刷新节点提示 |
| TCPing 超时 | 3000ms | 最低 500ms |
| URL Test 超时 | 3000ms | 最低 500ms |
| 节点IP信息超时 | 12000ms | 最低 1000ms |
| 单次下载测速超时 | 25000ms | 设为 0 则不限制 |
| TCPing 并发数 | 16 | 范围 1~128 |
| URL Test 并发数 | 10 | 范围 1~128 |
| 带宽测试并发数 | 1 | 范围 1~3，默认保持串行；提高并发可加快粗筛但会增加测速竞争 |
| 流媒体测试并发数 | 3 | 范围 1~32 |
| VPN MTU | 9000 | 范围 576~9000，修改后需断开重连 |

**设置位置**：侧边栏 → 其他配置

---

### 运行日志

运行日志用于用户反馈问题时导出必要诊断信息，入口位于侧边栏。

**功能特点**：

- 顶部提供刷新、分享、清空三个图标按钮
- 分享时生成 `FireflyVPN-runtime-日期-hash.log`，通过 `FileProvider` 分享
- 日志来源为 APP 内部专用 `RuntimeLog`，不直接导出 Android logcat
- 默认最多保留最新 1000 条日志；单条消息会截断，旧日志会自动滚动清理
- 仅记录脱敏后的关键 Info / Warn / Error，例如 APP 启动、VPN 启停、核心兼容校验、自动测试摘要、导入结果、更新/公告请求失败、sing-box warn/error 等
- 不输出节点链接、生成的 sing-box 配置、server/IP/domain/port、UUID/password/token/key、分应用代理包名列表等敏感信息

**设置位置**：侧边栏 → 运行日志

---

### 绕过局域网

开启后，局域网流量将绕过 VPN 直连，确保内网设备访问正常。

**绕过的 IP 范围**：
| IP 段 | 说明 |
|--------|------|
| `127.0.0.0/8` | 本地回环 (localhost) |
| `10.0.0.0/8` | A类私有网络 |
| `172.16.0.0/12` | B类私有网络 |
| `192.168.0.0/16` | C类私有网络 |
| `169.254.0.0/16` | 链路本地地址 |

**设置位置**：侧边栏 → 其他配置 → 网络 → 绕过局域网（默认开启）

---

### 局域网代理

局域网代理允许同一局域网内的电脑、平板或其他设备连接到手机 APP 的代理端口，通过当前选择的节点访问网络。适合临时让 PC 走手机上的节点代理。

**工作方式**：

- 需先选择节点并开启 VPN，sing-box 服务运行后才会启动局域网代理端口
- HTTP 代理使用页面显示的 HTTP 端口，SOCKS5 使用下一端口
- Windows 系统代理 / Edge 推荐使用 HTTP 端口；Firefox 手动代理、curl 或专业代理工具可使用 SOCKS5
- SOCKS5 测试建议使用 `socks5h://`，让 APP 侧解析域名，例如：

```bash
curl -I --proxy socks5h://手机局域网IP:SOCKS5端口 https://www.iwara.tv
```

**端口与认证说明**：

- 支持自动选择一组未占用端口，避免和其他服务冲突
- 普通 VPN 模式切换或重载不会因为自身旧监听未释放而随意跳端口
- 认证默认关闭；开启认证后，浏览器不会弹出用户名/密码提示，建议仅在支持预设凭证的工具中使用

**后台稳定性**：

- 页面内提供“忽略电池优化”状态检测与管理入口
- 长时间给其他设备做代理时，建议允许忽略电池优化
- 部分定制 ROM 仍可能需要额外开启自启动/后台运行/锁定后台等厂商设置

**设置位置**：侧边栏 → 局域网代理

---

### IPv6 路由

IPv6 路由功能允许用户控制 VPN 对 IPv6 网络的处理方式。

**四种模式**：

| 模式 | 说明 | 适用场景 |
|------|------|----------|
| **禁用** (默认) | 不使用 IPv6，所有流量走 IPv4 | 网络环境不支持 IPv6 时 |
| **启用** | 同时支持 IPv4 和 IPv6，优先 IPv4 | 需要 IPv6 但追求稳定性 |
| **优先** | 同时支持 IPv4 和 IPv6，优先 IPv6 | 希望尽量使用 IPv6 网络 |
| **仅** | 仅使用 IPv6 (实验性) | 测试纯 IPv6 环境 |

> ⚠️ **注意**：
> - 「仅」模式下，不支持 IPv6 的网站/服务将无法访问
> - 节点本身需要支持 IPv6 才能正常使用 IPv6 路由功能
> - 可通过 [test-ipv6.com](https://test-ipv6.com) 测试 IPv6 连通性

**设置位置**：侧边栏 → 其他配置 → 网络 → IPv6 路由

---

### 备用节点

备用节点功能允许运营者配置备用订阅源，当主订阅不可用或被封锁时，用户可以快速切换到备用源获取节点。

**功能特点**：
- 🔄 **一键切换**：侧边栏开关，快速切换主/备用订阅源
- 🛡️ **自动回退**：备用源请求失败时，自动关闭备用模式并恢复默认订阅
- 💾 **本地缓存**：备用节点 URL 会缓存到本地，确保下次启动时可用
- 🔔 **状态提示**：切换时自动断开现有连接，并 Toast 提示当前状态

**回退机制**：

以下情况会自动触发回退（关闭备用节点 → 清除缓存 → 恢复默认）：
- 备用订阅 URL 返回空响应或 HTTP 错误
- 备用订阅 URL 格式无效（非 http/https 开头）
- 公告配置中无 `backupNodes` 对象或无 `url` 属性

> ⚠️ **注意**：切换备用节点开关时，如果 VPN 正在运行，会自动断开连接并清除当前选中的节点。

**设置位置**：侧边栏 → 备用节点（仅在公告配置中包含有效 `backupNodes.url` 时显示）

**服务端配置**：参见下方 [公告通知接口](#3-公告通知接口) 中的 `backupNodes` 字段。

---

### 数据模型与本地存储变更

`Node` 模型新增了自动化测试相关字段：

- `downloadMbps`：下载带宽（Mbps）
- `uploadMbps`：上传带宽（Mbps，预留）
- `unlockSummary`：流媒体测试结果（可展示全量关键结果）
- `unlockPassed`：解锁筛选是否通过
- `autoTestStatus`：自动化阶段状态（如 `LATENCY_PASSED` / `BANDWIDTH_FILTERED` / `UNLOCK_PASSED`）
- `autoTestedAt`：自动化测试时间戳
- `source`：节点来源（`SUBSCRIPTION` / `FAVORITE`）
- `favoriteSourceNodeId`：从订阅节点收藏而来的来源节点 ID
- `favoriteCreatedAt`：收藏节点创建时间，用于收藏列表排序

`SettingsRepository` 自动化测试配置项：

- `autoTestEnabled`
- `autoTestFilterUnavailable`
- `autoTestLatencyEnabled`
- `autoTestLatencyMode`（URL Test / TCPing）
- `autoTestLatencyThresholdMs`
- `autoTestBandwidthEnabled`
- `autoTestBandwidthDownloadEnabled`
- `autoTestBandwidthUploadEnabled`
- `autoTestBandwidthDownloadThresholdMbps`
- `autoTestBandwidthUploadThresholdMbps`
- `autoTestBandwidthWifiOnly`
- `autoTestBandwidthDownloadSizeMb`
- `autoTestBandwidthUploadSizeMb`
- `autoTestUnlockEnabled`
- `autoTestByRegion`
- `autoTestNodeLimit`
- `preferTestModes`（测试偏好模式列表，JSON）
- `preferTestSelectedModeId`
- `startupDefaultTestMode`
- `startupDefaultTestChoiceDone`
- `nodeListCategory`（当前节点列表视图：主/备用节点或收藏节点）

`SettingsRepository` 用户可配置项（"其他配置"页面）：

- `tcpingTestTimeoutMs` — TCPing 超时（毫秒）
- `urlTestTimeoutMs` — URL Test 超时（毫秒）
- `nodeIpInfoTimeoutMs` — 节点 IP 信息查询超时（毫秒）
- `speedTestDownloadTimeoutMs` — 单次下载测速超时（毫秒）
- `tcpingConcurrency` — TCPing 并发数
- `urlTestConcurrency` — URL Test 并发数
- `bandwidthTestConcurrency` — 带宽测试并发数（1~3，默认 1）
- `unlockTestConcurrency` — 流媒体测试并发数
- `vpnMtu` — VPN MTU 值（修改后需断开重连）
- `nodeIpInfoTestOnVpnStart` — VPN 连接后是否自动获取节点 IP 信息
- `scheduledNodeUpdateEnabled` — 是否定时更新节点信息
- `scheduledNodeUpdateHours` — 定时更新间隔小时数（0~168）
- `scheduledNodeUpdateMinutes` — 定时更新间隔分钟数（0~59）
- `nodeAutoReconnect` — 节点更新后是否按 `server + port` 自动重连
- `scheduledNodeUpdateToastEnabled` — 定时更新节点信息后是否显示 Toast 提示
- `rememberLastSelectedNodeEnabled` — 是否记住上次选择的节点（默认开启）
- `lastSelectedNodeId` — 上次选择节点 ID
- `appThemeMode` — APP 主题模式（跟随系统 / 浅色 / 深色）

> ⚠️ 当前数据库使用 SQLCipher 加密存储（version 3），并配置了 `fallbackToDestructiveMigration()`。当 Room 版本升级时，会清空本地节点数据后重建。旧版明文数据库会在升级时自动检测并删除重建。

---

## 安全特性

本项目内置多层安全防护机制，防止 APK 被逆向分析、篡改或抓包复制订阅。

### 1. 字符串混淆 (StringFog)

使用 [StringFog](https://github.com/niceyun/gradle-stringfog-plugin) 插件对代码中的硬编码字符串进行加密混淆。

**效果**：反编译后无法直接看到 API 地址、密钥等敏感字符串。

**配置位置**：`app/build.gradle.kts`

```kotlin
configure<com.github.megatronking.stringfog.plugin.StringFogExtension> {
    implementation = "com.github.megatronking.stringfog.xor.StringFogImpl"
    enable = true
    fogPackages = arrayOf("xyz.a202132.app") // 只加密我们自己的代码
    kg = com.github.megatronking.stringfog.plugin.kg.RandomKeyGenerator()
    mode = com.github.megatronking.stringfog.plugin.StringFogMode.base64
}
```

---

### 2. NDK 密钥存储

AES 加密密钥存储在 Native (C++) 层，通过双数组 XOR + 运行时噪声混淆防止静态分析。

**密钥文件**：`app/src/main/cpp/native-lib.cpp`

#### 如何修改 AES 密钥

1. 确定你的 16 位密钥（AES-128 要求恰好 16 字节），例如：`MySecretKey12345`

2. 使用以下 Python 脚本生成混淆后的双数组：

```python
import os

key = "MySecretKey12345"  # 必须 16 字符
assert len(key) == 16

kXor = 0xA7  # XOR 常量，可自定义
partB = list(os.urandom(16))  # 随机生成 partB

# 计算 partA: 运行时 decoded[i] = partA[i] ^ partB[i] ^ kXor
partA = [ord(c) ^ partB[i] ^ kXor for i, c in enumerate(key)]

def fmt(arr, size=8):
    lines = []
    for i in range(0, len(arr), size):
        chunk = ", ".join(f"0x{v:02X}" for v in arr[i:i+size])
        lines.append(f"        {chunk}" + ("," if i + size < len(arr) else ""))
    return "\n".join(lines)

print(f"static const uint8_t partA[16] = {{\n{fmt(partA)}\n}};")
print(f"static const uint8_t partB[16] = {{\n{fmt(partB)}\n}};")
print(f"constexpr uint8_t kXor = 0x{kXor:02X};")
```

3. 将输出的 `partA`、`partB`、`kXor` 替换到 `native-lib.cpp` 中 `nativeGetNativeKey` 函数对应位置

4. **同步修改服务端加密密钥**

---

### 3. AES 流量加密

节点订阅数据在服务端加密后传输，APP 端使用 Java Crypto API 解密。

#### 服务端加密要求

| 参数 | 值 |
| :--- | :--- |
| **算法** | AES-128-GCM |
| **IV 长度** | 12 字节 (随机生成) |
| **认证标签** | 128 位 (16 字节) |
| **密钥** | 与 `native-lib.cpp` 中配置的相同（16 字节） |
| **输出格式** | Base64(IV + 密文 + AuthTag) |

#### 服务端加密流程

```
明文节点链接 → AES-GCM加密(生成随机IV) → 拼接(IV + 密文 + AuthTag) → Base64编码 → 返回给APP
```

#### Python 加密示例

```shell
pip install cryptography // 安装依赖
```

```python
import os
import base64
from cryptography.hazmat.primitives.ciphers.aead import AESGCM

# 密钥必须是 16 字节 (对应 AES-128)
SECRET_KEY = b'MySecretKey12345' 

def encrypt(plaintext):
    # 1. 初始化 AES-128-GCM 实例
    aesgcm = AESGCM(SECRET_KEY)
    
    # 2. 生成随机 12 字节 IV
    iv = os.urandom(12)
    
    # 3. 加密
    # cryptography 库的 encrypt 方法会自动生成 16 字节的 authTag 
    # 并将其附加在密文后面：返回值为 ciphertext + authTag
    ciphertext_with_tag = aesgcm.encrypt(iv, plaintext.encode('utf-8'), None)
    
    # 4. 拼接: IV (12) + 密文 + AuthTag (16)
    combined = iv + ciphertext_with_tag
    
    # 5. 返回 Base64 编码的字符串
    return base64.b64encode(combined).decode('utf-8')

# --- 使用示例 ---
nodes = """hysteria2://uuid@server:port?sni=example.com#节点名称
vless://uuid@server:port?security=tls#另一个节点"""

encrypted_data = encrypt(nodes)
print(encrypted_data)
```

---

### 4. 签名校验 (Signature Verification)

APP 启动时在 Native 层校验 APK 签名。如果签名不匹配（说明被重新签名/篡改），APP 会立即 Crash。

**签名文件**：`app/src/main/cpp/native-lib.cpp`

#### 如何设置签名 SHA-256

1. 获取你的 Release 签名证书 SHA-256 值：

```powershell
# 使用 Android Studio 自带的 JDK
& "C:\Program Files\Android\Android Studio\jbr\bin\keytool.exe" -list -v -keystore your-release-key.jks -alias your-alias
```

2. 复制输出中的 `SHA256:` 值（格式如 `95:CA:C5:8A:...`），去掉冒号得到 64 位十六进制字符串

3. 使用以下 Python 脚本生成混淆后的双数组：

```python
import os

# 将 SHA-256 输出的冒号去掉，转成大写
sha256_hex = "95CAC58A..."  # 替换为你的完整 64 位十六进制字符串
sha256_bytes = bytes.fromhex(sha256_hex)
assert len(sha256_bytes) == 32

kXor = 0x5D  # XOR 常量，可自定义
partB = list(os.urandom(32))  # 随机生成 partB

# 计算 partA: 运行时 expected[i] = partA[i] ^ partB[i] ^ kXor
partA = [sha256_bytes[i] ^ partB[i] ^ kXor for i in range(32)]

def fmt(arr, size=8):
    lines = []
    for i in range(0, len(arr), size):
        chunk = ", ".join(f"0x{v:02X}" for v in arr[i:i+size])
        lines.append(f"            {chunk}" + ("," if i + size < len(arr) else ""))
    return "\n".join(lines)

print(f"static const uint8_t partA[32] = {{\n{fmt(partA)}\n}};")
print(f"static const uint8_t partB[32] = {{\n{fmt(partB)}\n}};")
print(f"constexpr uint8_t kXor = 0x{kXor:02X};")
```

4. 将输出的 `partA`、`partB`、`kXor` 替换到 `native-lib.cpp` 中 `isExpectedSignature` 函数对应位置

5. 重新 Clean → Rebuild 项目

> ⚠️ **注意**：每次更换签名证书后，都需要更新此值，否则 APP 将无法启动。


---

### 5. Release 日志屏蔽

Release 版本默认移除所有 `android.util.Log` 调用（包括 `Log.d`、`Log.i`、`Log.w`、`Log.e`），通过 R8/ProGuard 在编译时优化。

**优点**：
- 减少 APK 体积
- 防止日志泄露敏感信息
- 提升运行性能

**配置位置**：`app/proguard-rules.pro`

```proguard
# 移除所有日志调用
-assumenosideeffects class android.util.Log {
    public static int d(...);
    public static int i(...);
    public static int v(...);
    public static int w(...);
    public static int e(...);
}
```

#### 如何保留部分日志

如果需要在 Release 版本中保留部分日志（如用于崩溃分析），可以注释掉对应级别：

```proguard
# 保留 Warning 和 Error 级别日志
-assumenosideeffects class android.util.Log {
    public static int d(...);
    public static int i(...);
    public static int v(...);
    # public static int w(...);  # 保留
    # public static int e(...);  # 保留
}
```

修改后需重新 Build Release 版本。

---

### 6. 网络安全配置

`network_security_config.xml` 控制应用的 HTTP 明文流量策略：

```xml
<network-security-config>
    <base-config cleartextTrafficPermitted="false">
        <trust-anchors>
            <certificates src="system" />
        </trust-anchors>
    </base-config>
    <domain-config cleartextTrafficPermitted="true">
        <domain includeSubdomains="true">your-domain.com</domain>
        <domain includeSubdomains="true">127.0.0.1</domain>  <!-- URL Test ClashAPI 本地通信 -->
    </domain-config>
</network-security-config>
```

> ⚠️ `127.0.0.1` 的明文放行是 URL Test 功能必需的（ClashAPI 使用 HTTP 协议通信），请勿移除。

---

### 7. 本地数据库加密 (SQLCipher)

本地节点数据库使用 [SQLCipher for Android](https://github.com/niceyun/sqlcipher-android) 进行加密存储，防止 Root 环境下节点数据被直接读取。

**工作原理**：

1. 首次启动时，`DatabasePassphraseManager` 生成随机 256-bit 数据库密钥
2. 密钥通过 Android Keystore 的 AES-GCM 加密后存储在 SharedPreferences 中
3. Room 通过 `SupportOpenHelperFactory` 使用该密钥打开加密数据库
4. 旧版明文数据库会被自动检测并删除重建（通过读取文件头判断是否为 SQLite 明文格式）

**核心文件**：
- `DatabasePassphraseManager.kt` — 密钥生成、加密存储、解密读取
- `AppDatabase.kt` — 加密数据库初始化 + 旧数据库迁移

> 💡 密钥由 Android Keystore 硬件保护，即使设备被 Root，攻击者也无法直接获取原始密钥。

---

## API 接口

### 1. 节点订阅接口

**端点**: `GET /api/nodes`

**响应格式**: Base64 编码的节点链接列表（每行一个）

**支持的协议**:
- `vless://` - VLESS
- `vmess://` - VMess 
- `trojan://` - Trojan
- `hysteria2://` 或 `hy2://` - Hysteria2
- `anytls://` - AnyTLS
- `tuic://` - TUIC
- `naive://` 或 `naive+https://` - Naive
- `wireguard://` - WireGuard
- `ss://` - Shadowsocks
- `socks://` 或 `socks5://` - SOCKS5
- `socks4://` - SOCKS4
- `http://` - HTTP 代理
- `https://` - HTTPS 代理 (自动启用 TLS)

**示例响应** (Base64 解码后):
```
vless://uuid@server:443?security=reality&type=tcp&sni=example.com#节点名称
vmess://eyJ2IjoiMiIsInBzIjoi5ZCN56ewIiwiYWRkIjoic2VydmVyLmNvbSIsInBvcnQiOiI0NDMifQ==
trojan://password@server:443?sni=example.com#Trojan节点
ss://YWVzLTI1Ni1nY206cGFzc3dvcmQ=@server:8388#SS节点
```

**配置位置**: `AppConfig.kt` → `SUBSCRIPTION_URL`

---

### 2. 版本更新接口

**端点**: `GET /api/update`

**响应格式**: JSON

```json
{
    "version": "1.1.0",
    "versionCode": 2,
    "is_force":0,
    "downloadUrl": "https://your-server.com/download/app-v1.1.0.apk",
    "changelog": "1. 新增智能分流功能\n2. 修复已知问题"
}
```

**字段说明**:
| 字段 | 类型 | 必填 | 说明 |
|------|------|------|------|
| `version` | String | ❌ | 版本号（显示用） |
| `versionCode` | Int | ✅ | 版本代码（用于比较） |
| `is_force` | Int | ❌ | 是否强制更新（1为强制更新） |
| `downloadUrl` | String | ❌ | APK 下载地址 |
| `changelog` | String | ❌ | 更新日志 |

**配置位置**: `AppConfig.kt` → `UPDATE_URL`

---

### 3. 公告通知接口

**端点**: `GET /api/notice`

**响应格式**: JSON

```json
{
    "hasNotice": true,
    "title": "系统公告",
    "content": "服务器将于今晚 22:00 进行维护，届时可能无法连接。",
    "noticeId": "notice_20240117",
    "showOnce": true,
    "backupNodes": {
        "msg": "主节点不可用时，请开启备用节点",
        "url": "https://your-server.com/api/backup-nodes"
    },
    "scheduledNodeUpdate": {
        "enabled": true,
        "hours": 6,
        "minutes": 0,
        "nodeAutoReconnect": true,
        "toastEnabled": true
    }
}
```

**字段说明**:
| 字段 | 类型 | 必填 | 说明 |
|------|------|------|------|
| `hasNotice` | Boolean | ✅ | 是否有公告 |
| `title` | String | ❌ | 公告标题 |
| `content` | String | ❌ | 公告内容，支持常见 HTML 标签（如 h1-h6、p、b、a、br、img 等），纯文本会自动按换行显示 |
| `noticeId` | String | ❌ | 公告唯一ID（用于去重） |
| `showOnce` | Boolean | ❌ | 是否只显示一次（默认 `true`） |
| `backupNodes` | Object | ❌ | 备用节点配置（可选） |
| `backupNodes.msg` | String | ❌ | 备用节点提示信息 |
| `backupNodes.url` | String | ❌ | 备用订阅 URL（必须以 `http://` 或 `https://` 开头） |
| `scheduledNodeUpdate` | Object | ❌ | 定时更新节点信息配置；存在时优先级高于本地设置 |
| `scheduledNodeUpdate.enabled` | Boolean | ❌ | 是否开启定时更新节点信息 |
| `scheduledNodeUpdate.hours` | Number | ❌ | 定时更新间隔小时数，范围 `0~168` |
| `scheduledNodeUpdate.minutes` | Number | ❌ | 定时更新间隔分钟数，范围 `0~59`；开启且小时/分钟均为 0 时 APP 会按 1 分钟处理 |
| `scheduledNodeUpdate.nodeAutoReconnect` | Boolean | ❌ | 是否开启节点自动重连；存在时优先级高于本地设置 |
| `scheduledNodeUpdate.toastEnabled` | Boolean | ❌ | 是否显示定时更新节点信息产生的 Toast；存在时优先级高于本地设置 |
| `nodeAutoReconnect` | Boolean | ❌ | 旧版兼容字段，推荐改用 `scheduledNodeUpdate.nodeAutoReconnect` |

> 💡 **备用节点说明**：
> - 当 `backupNodes.url` 存在且格式有效时，侧边栏会显示「备用节点」开关
> - 备用订阅的响应格式与主订阅相同（Base64 编码的节点链接列表）
> - 如果不需要备用节点功能，可省略整个 `backupNodes` 字段

> 💡 **定时更新说明**：
> - 计时从上次请求节点完成后开始；上次请求主节点则继续请求主节点，上次请求备用节点则继续请求备用节点
> - `scheduledNodeUpdate.nodeAutoReconnect` 开启后，仅当当前连接节点在新列表中存在相同 `server + port` 时才自动重连，否则保持原连接
> - `scheduledNodeUpdate.toastEnabled` 只控制定时更新节点信息产生的 Toast，不影响手动刷新节点提示
> - notice 接口下发的 `scheduledNodeUpdate` 只覆盖运行时有效设置，不会改写用户本地保存值

**配置位置**: `AppConfig.kt` → `NOTICE_URL`

---

## 自定义

### 修改应用主题颜色

**文件**: `app/src/main/java/xyz/a202132/app/ui/theme/Color.kt`

项目使用青绿色系主题，修改 `Color.kt` 中的颜色变量即可全局更改主题色：

```kotlin
// Primary Colors - Cyan/Teal Theme (matching firefly images)
val Primary = Color(0xFF00BFA5)          // 青绿主色
val PrimaryVariant = Color(0xFF00897B)   // 深青绿
val Secondary = Color(0xFF26C6DA)        // 亮青色
// ...
```

---

### 修改应用名称

**文件**: `app/src/main/res/values/strings.xml`

```xml
<string name="app_name">你的应用名称</string>
<string name="vpn_notification_title">你的应用名称运行中</string>
```

**文件**: `app/ui/screens/MainScreen.kt`

```
text = "流萤加速器"; 替换成你的应用名称
```

---

### 修改 VPN 连接按钮

当前连接按钮使用三张自定义图片表示不同状态：

| 图片文件 | 状态 | 说明 |
|---------|------|------|
| `btn_disconnected.png` | 未连接 | 默认待机状态 |
| `btn_connecting.png` | 连接中/断开中 | 带脉冲动画 |
| `btn_connected.png` | 已连接 | VPN 已开启 |

**图片位置**: `app/src/main/res/drawable/`

#### 替换按钮图片

将你的三张图片重命名为上述文件名，替换到 `drawable` 目录即可。

> 💡 推荐使用 **透明背景的 PNG 图片**，尺寸建议 512×512 像素以上以保证清晰度。

---

### 修改应用图标

**图标文件位置**:
```
app/src/main/res/
├── drawable/
│   ├── ic_launcher_background.xml  # 图标背景
│   └── ic_launcher_foreground.xml  # 图标前景
├── mipmap-anydpi-v26/
│   ├── ic_launcher.xml             # 自适应图标配置
│   └── ic_launcher_round.xml       # 圆形图标配置
└── mipmap-*/                        # 各分辨率位图（可选）
```

**推荐方式**: 使用 Android Studio 的 **Image Asset Studio**
1. 右键 `res` → New → Image Asset
2. 选择 Launcher Icons
3. 配置前景/背景图像
4. 自动生成所有尺寸

---

### 修改应用包名

需要修改以下位置：

1. **`app/build.gradle.kts`**:
```kotlin
android {
    namespace = "com.your.package"
    defaultConfig {
        applicationId = "com.your.package"
    }
}
```

2. **`AndroidManifest.xml`**: 确保 package 声明正确

3. **源代码目录**: 重构 `app/src/main/java/xyz/a202132/app/` 为新包名路径

4. **所有 Kotlin 文件**: 更新 `package` 声明

---

### 修改应用版本号

**文件**:**`app/build.gradle.kts`**:

```kotlin
versionCode = 15
versionName = "1.14.0"
```

版本号规范建议：
versionCode — 整数，每次发布必须递增，用于 Google Play 和系统判断新旧版本
versionName — 字符串，格式通常为 主版本.次版本.修订号（如 1.1.0）

---

### 修改主题颜色

**文件**: `app/src/main/res/values/themes.xml`

```xml
<style name="Theme.FireflyVPN" parent="android:Theme.Material.Light.NoActionBar">
    <item name="android:colorPrimary">@color/your_primary</item>
    <item name="android:colorAccent">@color/your_accent</item>
</style>
```

或在 Compose 主题文件中修改 Material 3 颜色方案。

------

### 自定义网络工具箱

**文件**: `app/src/main/java/xyz/a202132/app/AppConfig.kt`

修改 `NETWORK_TOOLS_JSON` 数组，按照以下格式添加或修改工具项：

```json
{"name": "工具名称", "url": "https://example.com", "icon": "icon_key"}
```

如需添加新的图标类型，需同时修改 `NetworkToolboxDialog.kt` 中的 `getToolIcon()` 函数。

---

## 构建发布

### Debug 构建

Debug 模式已配置使用 Release 签名（防止 Native 签名验证失败）：

```bash
./gradlew assembleDebug
```

输出: `app/build/outputs/apk/debug/app-debug.apk`

> ⚠️ **注意**: 由于 Native 层有签名校验，Debug 和 Release 构建均需使用相同的签名密钥。`build.gradle.kts` 中已配置 `debug { signingConfig = signingConfigs.getByName("release") }`。

### Release 构建

> ⚠️ **注意**: `keystore.properties` 和 `*.jks` 签名文件已被 `.gitignore` 忽略，构建 Release 版本需要你配置自己的签名。

1. **准备签名文件**:
   生成一个新的 `.jks` 签名文件（或使用现有的），放在项目根目录。

2. **创建配置文件**:
   在项目根目录创建 `keystore.properties` 文件：

```properties
keyAlias=你的KeyAlias
keyPassword=你的KeyPassword
storeFile=你的签名文件.jks
storePassword=你的StorePassword
```

3. **执行构建**:
```bash
./gradlew assembleRelease
# Windows PowerShell:
.\gradlew assembleRelease
```

**备选方法 (IDE 界面操作)**:
1. 菜单栏点击 **Build** -> **Generate Signed Bundle / APK**
2. 选择 **APK** -> **Next**
3. 选择密钥库并输入密码
4. 选择 **release** -> **Create**

输出: `app/build/outputs/apk/release/app-release.apk`

### 16 KB 页面对齐

自 2025 年 11 月起，Google Play 要求所有面向 Android 15+ 的应用支持 16 KB 页面大小。项目已在 `CMakeLists.txt` 中配置对齐：

```cmake
target_link_options(native-lib PRIVATE "-Wl,-z,max-page-size=16384")
```

> 💡 如果使用第三方 `.so` 库（如 `libbox.so`），也需确保其支持 16 KB 对齐，否则需更新上游库版本。

---

## 其他说明

### 智能分流实现

当前智能分流已基于 `rule_set` + `.srs` 文件：

- `SingBoxConfigGenerator` 在 SMART 模式引用 `geosite-cn` / `geoip-cn`
- `route.rule_set` 使用本地 `geosite-cn.srs` / `geoip-cn.srs`
- APP 启动后后台更新规则集：`VpnApplication` → `RuleManager.updateRuleSets()`
- VPN 启动/重启前确保规则集存在：`BoxVpnService` → `RuleManager.ensureRuleSets()`
- `ensureRuleSets()` 缺失时会从 assets 兜底拷贝

---

### 节点来源与核心配置校验

- 主/备用节点与收藏节点按 `NodeSource` 独立存储，收藏节点不会被订阅刷新覆盖
- 节点列表当前视图由 `nodeListCategory` 记录，三点菜单测试、择优面板和 VPN 启动都会按当前来源取节点
- 收藏导入时会先做解析、去重和 sing-box 单节点配置校验；不兼容核心的节点会被跳过
- VPN 启动/重启前会再次按当前来源过滤核心不支持的节点，并对最终完整配置执行 `Libbox.checkConfig()`
- 若当前选中的节点不被核心支持，APP 会提示错误并停止启动，不会自动切换到其他节点

---

### 测试与请求节点互斥

项目已实现"全局测试互斥 + 拉节点状态互斥"：

- 拉节点中禁止关键测试启动
- 测试进行中禁止拉节点
- 统一提示文案已细化为阶段型提示（如：TCPing/URL Test/解锁/测试择优进行中，请稍后；请求节点中，请稍后）

---

### 请求容错与自动重试

节点请求、公告通知、版本更新三类网络请求均具备统一的容错策略：

- 第一次请求失败/超时 → 自动重试一次（Toast 提示"请求失败，已自动重试..."）
- 第二次仍失败：
  - **节点请求（备用模式）**→ 关闭备用节点 → 清除缓存 → 恢复默认订阅
  - **节点请求（默认模式）**→ Toast 显示错误信息
  - **公告/更新请求** → Toast进行提示，不影响 APP 使用

**URL Test 自动重试**：仅对 HTTP 503 / 504 或请求异常自动重试 1 次（`URL_TEST_RETRY_COUNT`），200 但 delay 非法不会重试。

**节点 IP 信息自动重试**：仅对超时、网络异常（IOException）或 HTTP 429 / 500 / 502 / 503 / 504 自动重试 1 次（`NODE_IP_INFO_RETRY_COUNT`），重试间隔 300ms。

超时时间统一在 `AppConfig.kt` 配置：

| 配置项 | 默认值 | 说明 |
|--------|--------|------|
| `NODE_REQUEST_TIMEOUT_MS` | 25000 | 节点请求超时（毫秒） |
| `NOTICE_REQUEST_TIMEOUT_MS` | 25000 | 公告请求超时（毫秒） |
| `UPDATE_REQUEST_TIMEOUT_MS` | 25000 | 更新请求超时（毫秒） |
| `URL_TEST_RETRY_COUNT` | 1 | URL Test 重试次数（仅 503/504/异常） |
| `NODE_IP_INFO_RETRY_COUNT` | 1 | 节点 IP 信息重试次数（仅超时/网络异常/服务端错误） |

---

### 择优面板补充

- 自动化测试结果使用快照（`autoTestResultSnapshot`），避免后续刷新节点导致结果视图被"旧/新数据混合"污染
- "自动连接最优"按快照和当前优选规则执行（延迟优先/下行优先/解锁优先）

---

### 稳定性与下载行为

- 请求节点等待超时路径已改为可恢复处理（超时提示 + 自动重试），避免因等待阶段超时直接崩溃
- `DownloadManager` 对 HTTP 416 采用"非递归一次自动恢复策略"：
  - 先清理临时文件并全量重试一次
  - 仍失败再提示用户重试
  - 避免递归导致潜在栈风险

---

### 安全说明（务必阅读）

- 订阅解析日志已减少敏感信息输出，不再记录完整节点链接原文
- 运行日志使用 APP 内部专用日志仓库，写入前会脱敏 URL、代理链接、IP、域名、UUID、密码、token、key 等敏感片段
- 分享的运行日志文件生成在缓存目录，仅用于用户主动分享问题诊断信息
- Native 层密钥与签名目标值已做运行时重组，降低"直接明文检索"命中概率
- 但这类客户端静态保护仅能提升逆向成本，不能替代真正的密钥托管与服务端校验策略

---

## 开源协议

本项目基于 [GNU General Public License v3.0](LICENSE) 开源，与核心依赖 sing-box 的协议保持一致。

**依赖项目**:

- [sing-box](https://github.com/SagerNet/sing-box) - GPLv3
- [UnlockTests](https://github.com/oneclickvirt/UnlockTests) - Apache-2.0

---

## 致谢

- [SagerNet/sing-box](https://github.com/SagerNet/sing-box) - VPN 核心
- [UnlockTests](https://github.com/oneclickvirt/UnlockTests) - 流媒体解锁测试
- [JetBrains/Kotlin](https://github.com/JetBrains/kotlin) - Kotlin 语言
- [Google/Jetpack Compose](https://developer.android.com/jetpack/compose) - UI 框架
