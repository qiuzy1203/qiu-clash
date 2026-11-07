# qiu-clash

个人自用配置库：FlClash 覆写脚本 + Surge 模块。

---

## 一、FlClash 覆写脚本

基于 Smart-Config-Kit v6.0.21 修改。

**脚本地址（Windows 电脑用，复制这一行）**

```
https://raw.githubusercontent.com/qiuzy1203/qiu-clash/main/flclash-qiu.js
```

**脚本地址（三星安卓手机用，复制这一行）**

```
https://raw.githubusercontent.com/qiuzy1203/qiu-clash/main/flclash-qiu-android.js
```

> ⚠️ 两个脚本必须按设备选对，**不要混用**：
>
> | | `flclash-qiu.js` | `flclash-qiu-android.js` |
> |---|---|---|
> | 设备 | Windows 电脑 | 三星安卓手机 |
> | `dns.ipv6` | `true` | `false` |
> | `fake-ip-range6` | `2600:fe:dcba:9876::/64` | 无 |
> | 适用原因 | Windows 的 tun0 能拿到 IPv6 地址与路由，公网 IPv6 走 TUN 不泄漏 | Android VPNService 的 tun0 无全局 IPv6 地址、无 IPv6 路由；若 `dns.ipv6=true`，AAAA 会解析到无路由的 fake-ip 段 → AAAA 黑洞 |
>
> 其余分流规则、代理组、规则集两版**完全一致**（220 条规则 / 38 个代理组）。
>
> 为什么不做成一份脚本自动判断平台：FlClash 脚本运行在 QuickJS 沙盒
> （`rquickjs`，`Context::full`），只有标准 JS 全局，没有 `process` /
> `navigator` / `os`，脚本内无法可靠识别操作系统，故按平台拆成两个文件。

**使用**

1. FlClash → 配置 → 覆写脚本 → 新建 → URL 填对应设备的地址（Windows 填第一条，手机填第二条）
2. 关联到订阅 → 下拉刷新
3. 本仓库更新后，各设备点「更新脚本」拉取（脚本不会自动更新）
4. 换设备时记得换脚本地址——Windows 误用 android 版会失去 IPv6 代理能力

**本地修改**

- 番茄小说 / 字节系域名强制直连
- MiniMax 国际版（minimax.io）强制走代理
- 绿联 NAS（ugreen.com / ugnas.com / ugnas.cloud / ug.link）强制直连

---

## 二、Surge 模块（QiuH 去广告 | Block Ads 精准版）

基于 thNylHx/Tools 的 Blockads 模块裁剪：删除针对淘宝 / 抖音 / 微信 / QQ 的域名封杀与大厂接口整包替换，保留 1119 条 jq 字段级改写。

**模块地址（复制这一行）**

```
https://raw.githubusercontent.com/qiuzy1203/qiu-clash/main/Blockads-QiuH.sgmodule
```

**使用**

1. Surge → 模块 → 右上 `+` → 从 URL 安装 → 粘贴上面的地址
2. 启用模块
3. 需先在本机生成并信任 MITM 证书（设置 → MITM → 生成证书 → 安装描述文件 → 证书信任设置里打开完全信任）

---

## 注意

- 脚本内的 149 个规则集仍从上游 Smart-Config-Kit 实时拉取，本仓库只托管脚本本体。
- 本仓库是公开的，**不要往里放订阅链接、密码、密钥等敏感信息**。
