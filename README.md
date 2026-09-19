# 愛姉妹 PC-98 逆向工具集 / Aishima Tools Index

Silky's《愛姉妹》(1994, PC-98) 资源逆向工具的入口页。
全部工具在浏览器本地运行，不上传任何数据。

▶ 在线入口：<https://dragonxash.github.io/aishima-tools/>

★ 一体工具箱（推荐，单文件离线网页）：
<https://dragonxash.github.io/aishima-tools/pc98-toolbox.html>

## 工具清单

| # | 工具 | 说明 | 地址 |
|---|---|---|---|
| 00 | **PC-98 一体工具箱** ★ | 单文件离线网页：HDI/HDM/FDI 镜像读写 + DAT 解包 + GP4 渲染 + MES 解码 | [pc98-toolbox.html](https://dragonxash.github.io/aishima-tools/pc98-toolbox.html) |
| 01 | SILK.DAT 解包器 | 解包 sksdat 归档（XOR 索引表），文件列表 + ZIP 下载 | [elf-dat-extra](https://dragonxash.github.io/elf-dat-extra/) |
| 02 | MES 剧本预览器 | .MES 字典表 + 全文解码 | [aishima-mes-to-text](https://dragonxash.github.io/aishima-mes-to-text/) |
| 03 | GP4 图片预览器 | .GP4 直接渲染 + 下载 PNG/MAG | [gp4-viewer](https://dragonxash.github.io/gp4-viewer/) |
| 04 | GP4 → MAG 转换 | 已并入一体工具箱（GP4 预览页的「转 MAG」按钮） | — |

## 一体工具箱能做什么

`pc98-toolbox.html` 是一个自包含的 HTML 文件（约 84 KB，零依赖、不联网），
把镜像工具和格式预览器合成了一条链路：

- **磁盘镜像**：HDI（Anex86，4096 字节头）/ FDI / HDM（裸软盘）等，
  FAT12/16 自动探测分区位置、逻辑扇区大小（256/512/1024）、簇大小。
  支持目录浏览、单文件下载、整盘打包 ZIP，以及**写**（导入 / 删除文件后导出新镜像）。
- **格式预览器**：拖入任意文件即按内容嗅探类型 ——
  `SILK?.DAT` 归档（可继续下钻到里面的条目）、`.GP4` 图片（渲染 + 导出 PNG/MAG）、
  `.MES` 剧本（字典表 + 全文）、其余走 Shift-JIS 文本 / 十六进制视图。
- 原镜像与源文件永不被修改，改动只存在内存里，保存时输出新文件。

### 已修复的坑（本仓库内的版本）

| 问题 | 症状 | 原因 |
|---|---|---|
| `isSksdat` 签名校验过严 | `**** With mdataX.exe ver 1.02 ...` 版本的 SILK0.DAT 完全打不开 | 签名被固定要求出现在偏移 0；该发行版前面多了 `**** ` 装饰前缀。改为在前 8 字节内搜索签名（索引表位置和种子规则都不变） |
| `looksGP4` 调色板校验错误 | 实测 69/69 个真实 GP4 全部识别失败 | 原判据要求调色板 16 个色值低 2 位为 0，真实文件并不满足（如 `0x3415`）。改为只要求色值不全同 |
| 嗅探路由被内容误判带偏 | `.S4`（场景表）结构碰巧像 GP4，被渲染成花屏 | 改为**扩展名优先**，并加已知不可解码扩展名白名单；只有扩展名不认识时才做内容嗅探 |

## 文件链路

```
SILK?.DAT ──解包──▶ .MES 剧本（字典压缩）／ .GP4 图片（MTF/RLE）／ .S4 .M
```

## 相关链接

- [PC-98 HDI 解包器](https://dragonxash.github.io/pc98-hdi-explorer/)
- [GitHub 主页](https://github.com/dragonxash)
