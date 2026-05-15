---
name: herb
description: Generate a new herb guide HTML page for 1-3 Chinese medicinal herbs. Trigger when user types /herb followed by 1-3 Chinese herb names (e.g. /herb 黄芪 当归 党参). Scans existing herbs-XX-*.html files to determine the next sequence number, calls the Anthropic API to generate matching HTML content, saves the file, and reports the filename to the user.
---

# Herb Page Generator

## Trigger

User types `/herb` followed by 1 to 3 Chinese herb names separated by spaces.

Examples:
- `/herb 黄芪`
- `/herb 黄芪 当归`
- `/herb 黄芪 当归 党参`

## Step 1 — Parse herb names

Extract the herb names from the user's input after `/herb`. There will be 1, 2, or 3 names. Store them as a list, e.g. `["黄芪", "当归", "党参"]`.

## Step 2 — Determine the next sequence number

Use the Glob tool (pattern `herbs-*.html`) in the project directory `E:/AIProject/01-Agriculture-Plants/ai-xhs-zhongyaocai/` to list all existing herb pages. Parse the two-digit number from each filename (e.g. `herbs-14-...html` → 14). The next sequence number is `max + 1`, zero-padded to two digits (e.g. 15 → `15`).

## Step 3 — Build the output filename

Convert each herb name to its pinyin romanization (lowercase, no tones, no spaces). Join with hyphens.

Examples:
- 黄芪 → huangqi
- 当归 → danggui
- 党参 → dangshen
- 白术 → baizhu
- 茯苓 → fuling
- 甘草 → gancao
- 川芎 → chuanxiong
- 熟地黄 → shudaihuang
- 陈皮 → chenpi
- 半夏 → banxia
- 柴胡 → chaihu
- 枸杞 → gouqi
- 菊花 → juhua
- 金银花 → jinyinhua
- 连翘 → lianqiao
- 薄荷 → bohe
- 紫苏 → zisu
- 桑叶 → sangye
- 山楂 → shanzha
- 决明子 → juemingzi

For any herb not in the list above, use your knowledge to produce the standard pinyin romanization.

Filename format: `herbs-{XX}-{pinyin1}-{pinyin2}-{pinyin3}.html`

If only 1 or 2 herbs are provided, omit the missing pinyin segments.

Examples:
- 3 herbs 黄芪 当归 党参, next number 15 → `herbs-15-huangqi-danggui-dangshen.html`
- 2 herbs 白术 茯苓, next number 16 → `herbs-16-baizhu-fuling.html`
- 1 herb 甘草, next number 17 → `herbs-17-gancao.html`

## Step 4 — Generate HTML via Anthropic API

Call the Anthropic API using model `claude-haiku-4-5-20251001` with the following prompt. Fill in the placeholders before sending.

**System prompt:**
```
你是一位中医药科普作家，擅长用简洁生动的语言介绍中草药知识。请严格按照用户提供的HTML模板格式输出完整的HTML页面，不要添加任何解释文字，只输出HTML代码。
```

**User prompt (fill in HERB_LIST and FILENAME):**
```
请为以下中草药生成一个HTML科普页面：{HERB_LIST}

文件名将保存为：{FILENAME}

请严格按照以下HTML模板格式输出，每种草药对应一个card div。只输出完整的HTML，不要有任何其他文字：

<!DOCTYPE html>
<html>
<head>
    <style>
        body {
            font-family: 'Segoe UI', Arial, sans-serif;
            background: #f5f5f5;
            padding: 20px;
            position: relative;
        }
        .container {
            max-width: 600px;
            margin: auto;
        }
        .card {
            background: white;
            border-radius: 15px;
            padding: 20px;
            margin: 15px 0;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
        }
        h1 {
            color: #2d5f4a;
            text-align: center;
        }
        h2 {
            color: #4CAF50;
            margin-top: 0;
        }
        .plant-img {
            width: 100%;
            height: 200px;
            border-radius: 10px;
            object-fit: cover;
            margin: 10px 0;
        }
        .tag {
            display: inline-block;
            background: #e8f5e9;
            color: #2d5f4a;
            padding: 5px 10px;
            border-radius: 20px;
            font-size: 0.9em;
            margin: 5px;
        }
        .screenshot-button {
            position: absolute;
            top: 10px;
            right: 10px;
            background-color: #4CAF50;
            color: white;
            border: none;
            padding: 10px 15px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 14px;
        }
        .screenshot-button:hover {
            background-color: #3e8e41;
        }
        .back-button {
            position: absolute;
            top: 10px;
            left: 10px;
            background-color: #666;
            color: white;
            border: none;
            padding: 10px 15px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 14px;
            text-decoration: none;
            display: inline-block;
        }
        .back-button:hover {
            background-color: #555;
        }
    </style>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>
</head>
<body>
    <a href="index.html" class="back-button">← 返回首页</a>
    <button class="screenshot-button" onclick="captureScreenshot()">📸 截图</button>

    <div class="container">
        <h1>🌿路边本草图鉴 | 三步识药材</h1>

        <!-- 为每种草药生成一个card，格式如下 -->
        <div class="card">
            <h2>[草药名] | [简短别称或功效标签]</h2>
            <div class="plant-img" style="background: #e8f5e9; text-align: center">
                <img width="100%" height="200px" src="">
            </div>
            <p>[2-3句话描述：外形特征、主要功效、常见用法]</p>
            <div class="tag">📌[生长环境或来源]</div>
            <div class="tag">💊[主要有效成分]</div>
        </div>

        <p style="text-align: center; color: #666; font-size: 0.9em;">🌱遇见请珍惜 勿过度采摘 | 药用请遵医嘱</p>
    </div>

    <script>
        function captureScreenshot() {
            html2canvas(document.body).then(function(canvas) {
                const imgData = canvas.toDataURL('image/png');
                const link = document.createElement('a');
                link.href = imgData;
                link.download = 'screenshot.png';
                document.body.appendChild(link);
                link.click();
                document.body.removeChild(link);
            });
        }
    </script>
</body>
</html>

要求：
1. 每种草药生成一个card div
2. h2格式：草药名 | 简短功效标签（如"清热解毒根"、"补气固表草"）
3. img的src留空字符串即可
4. p标签内容：2-3句话，包含外形特征、主要功效、常见用法
5. 第一个tag描述生长环境或药材来源（加📌）
6. 第二个tag描述主要有效成分（加💊）
7. 保留页面底部的安全提示文字
8. 只输出HTML代码，不要有任何解释
```

Replace `{HERB_LIST}` with the herb names joined by `、` (e.g. `黄芪、当归、党参`).
Replace `{FILENAME}` with the computed filename (e.g. `herbs-15-huangqi-danggui-dangshen.html`).

## Step 5 — Save the file

Use the Write tool to save the API response (the HTML string) to:

`E:/AIProject/01-Agriculture-Plants/ai-xhs-zhongyaocai/{FILENAME}`

## Step 6 — Report to the user

Tell the user:

1. The filename that was saved (e.g. `herbs-15-huangqi-danggui-dangshen.html`)
2. A reminder to add a card entry to `index.html` so the new page appears on the homepage

Example report:
```
已生成并保存：herbs-15-huangqi-danggui-dangshen.html

请记得在 index.html 中添加对应的卡片条目，让新页面出现在首页列表中。
```
