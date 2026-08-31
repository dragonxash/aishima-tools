# 愛姉妹 PC-98 逆向工具集 / Aishima Tools Index

Silky's《愛姉妹》(1994, PC-98) 资源逆向工具的入口页。
全部工具在浏览器本地运行，不上传任何数据。

▶ 在线入口：<https://dragonxash.github.io/aishima-tools/>

## 工具清单

| # | 工具 | 说明 | 地址 |
|---|---|---|---|
| 01 | SILK.DAT 解包器 | 解包 sksdat 归档（XOR 索引表），文件列表 + ZIP 下载 | [elf-dat-extra](https://dragonxash.github.io/elf-dat-extra/) |
| 02 | MES 剧本预览器 | .MES 字典表 + 全文解码 | [aishima-mes-to-text](https://dragonxash.github.io/aishima-mes-to-text/) |
| 03 | GP4 图片预览器 | .GP4 直接渲染 + 下载 PNG/MAG | [gp4-viewer](https://dragonxash.github.io/gp4-viewer/) |
| 04 | MAG 批量转换 | GP4→MAG 命令行工具（MAKI02） | `gp4_to_mag.py` |

## 文件链路

```
SILK?.DAT ──解包──▶ .MES 剧本（字典压缩）／ .GP4 图片（MTF/RLE）／ .S4 .M
```

## 相关链接

- [PC-98 HDI 解包器](https://dragonxash.github.io/pc98-hdi-explorer/)
- [GitHub 主页](https://github.com/dragonxash)
