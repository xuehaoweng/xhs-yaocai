# 🌿 路边本草图鉴 - 三步识药材

> 帮助人们快速识别和了解身边的中草药，传承中华医药文化。

[![Deploy to GitHub Pages](https://github.com/xuehaoweng/xhs-yaocai/actions/workflows/deploy.yml/badge.svg)](https://github.com/xuehaoweng/xhs-yaocai/actions/workflows/deploy.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

**在线访问：** https://xuehaoweng.github.io/xhs-yaocai

[![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/xuehaoweng/xhs-yaocai)
[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https://github.com/xuehaoweng/xhs-yaocai)

---

## 项目特色

- **三步识别法**：形态特征、生长环境、药用价值三维度快速识别
- **14 组图鉴**：涵盖 42 种路边常见中草药
- **AI 生成器**：输入草药名，自动生成图鉴页面（需要 Anthropic API Key）
- **一键截图**：将图鉴保存为图片分享
- **响应式设计**：手机和电脑均可流畅使用

## 快速开始

### 方式一：直接访问在线版

打开 https://xuehaoweng.github.io/xhs-yaocai 即可使用。

### 方式二：一键部署到自己的账号

点击上方 "Deploy to Netlify" 或 "Deploy with Vercel" 按钮，fork 并部署到自己的域名。

### 方式三：本地运行

```bash
git clone https://github.com/xuehaoweng/xhs-yaocai.git
cd roadside-herb-guide
npm install
npm run dev
```

浏览器访问 http://localhost:8000

## AI 草药生成器

网站内置 AI 生成器，输入草药名称即可自动生成图鉴页面：

1. 打开网站，找到页面底部的 **AI 生成器** 区域
2. 填入你的 [Anthropic API Key](https://console.anthropic.com/)（仅存储在本地浏览器，不会上传）
3. 输入 1-3 个草药名称，点击生成
4. 预览结果，一键下载 HTML 文件

## 药材目录（14 组 · 42 种）

| 组 | 药材 | 文件 |
|---|---|---|
| 第一组 | 车前草、蒲公英、艾草 | [herbs-01](herbs-01-cheqiancao-pugongying-aicao.html) |
| 第二组 | 紫苏、薄荷、金银花 | [herbs-02](herbs-02-zisu-bohe-jinyinhua.html) |
| 第三组 | 凤仙花、三七、田七 | [herbs-03](herbs-03-fengxianhua-sanqi-tianqi.html) |
| 第四组 | 夏枯草、益母草、马齿苋 | [herbs-04](herbs-04-xiakucao-yimucao-machixian.html) |
| 第五组 | 桔梗、虎杖、鱼腥草 | [herbs-05](herbs-05-jiegeng-huzhang-yuxingcao.html) |
| 第六组 | 灯心草、苍耳子、龙葵 | [herbs-06](herbs-06-dengxincao-cangerzi-longkui.html) |
| 第七组 | 板蓝根、连翘、野菊花 | [herbs-07](herbs-07-banlangen-lianqiao-yejuhua.html) |
| 第八组 | 决明子、山楂、枸杞 | [herbs-08](herbs-08-juemingzi-shanzha-gouqi.html) |
| 第九组 | 白茅根、芦根、淡竹叶 | [herbs-09](herbs-09-baimaogen-lugen-danzhuye.html) |
| 第十组 | 桑叶、桑葚、桑白皮 | [herbs-10](herbs-10-sangye-sangshen-sangbaipi.html) |
| 第十一组 | 槐花、槐角、槐米 | [herbs-11](herbs-11-huaihua-huaijiao-huaimi.html) |
| 第十二组 | 菊花、金银花、玫瑰花 | [herbs-12](herbs-12-juhua-jinyinhua-meiguihua.html) |
| 第十三组 | 陈皮、青皮、橘红 | [herbs-13](herbs-13-chenpi-qingpi-juhong.html) |
| 第十四组 | 酸枣仁、柏子仁、火麻仁 | [herbs-14](herbs-14-suanzaoren-baiziren-huomaren.html) |

## 项目结构

```
roadside-herb-guide/
├── index.html                    # 主页（含 AI 生成器）
├── herbs-01-*.html               # 各组药材图鉴页面
├── ...
├── .github/workflows/deploy.yml  # GitHub Pages 自动部署
├── netlify.toml                  # Netlify 部署配置
├── vercel.json                   # Vercel 部署配置
├── package.json
└── README.md
```

## 贡献指南

欢迎提交 Issue 和 Pull Request！

- 新增药材页面：参考现有 `herbs-XX-*.html` 格式，文件名使用拼音
- 修正内容错误：直接提 PR，注明来源
- 功能建议：先开 Issue 讨论

详见 [CONTRIBUTING.md](CONTRIBUTING.md)

## 安全提醒

> ⚠️ 遇见请珍惜，勿过度采摘。药用请遵医嘱，不可自行服用。部分药材可能有毒性，请在专业人士指导下使用。

## 许可证

[MIT License](LICENSE) © 2024 路边本草图鉴项目
