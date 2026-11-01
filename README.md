# qiu-clash

个人自用配置库：FlClash 覆写脚本 + Surge 模块。

---

## 一、FlClash 覆写脚本

基于 Smart-Config-Kit v6.0.21 修改。

**脚本地址（复制这一行）**

```
https://raw.githubusercontent.com/qiuzy1203/qiu-clash/main/flclash-qiu.js
```

**使用**

1. FlClash → 配置 → 覆写脚本 → 新建 → URL 填上面的地址
2. 关联到订阅 → 下拉刷新
3. 本仓库更新后，各设备点「更新脚本」拉取（脚本不会自动更新）

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
