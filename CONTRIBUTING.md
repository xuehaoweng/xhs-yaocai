# 贡献指南

感谢您对路边本草图鉴项目的关注！我们欢迎所有形式的贡献。

## 如何贡献

### 1. 报告问题

如果您发现了问题或有改进建议，请通过以下方式联系我们：

- 在GitHub上提交Issue
- 发送邮件到项目维护者

### 2. 提交代码

如果您想贡献代码，请遵循以下步骤：

1. Fork本项目
2. 创建您的特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交您的更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 打开一个Pull Request

### 3. 添加新药材

如果您想添加新的药材图鉴，请：

1. 准备高质量的药材图片
2. 收集准确的药材信息（形态特征、生长环境、药用价值）
3. 按照现有模板创建HTML文件
4. 更新README.md中的药材目录
5. 提交Pull Request

### 4. 改进文档

我们欢迎对文档的改进，包括：

- 修正错别字和语法错误
- 添加更多使用说明
- 改进项目结构说明
- 翻译成其他语言

## 开发环境设置

1. 克隆项目：
```bash
git clone https://github.com/xuehaoweng/xhs-yaocai.git
cd roadside-herb-guide
```

2. 安装依赖（可选）：
```bash
npm install
```

3. 启动本地服务器：
```bash
npm start
# 或者
python -m http.server 8000
```

4. 在浏览器中打开 `http://localhost:8000`

## 代码规范

- 使用UTF-8编码
- HTML文件使用2个空格缩进
- CSS使用2个空格缩进
- JavaScript使用2个空格缩进
- 文件名使用中文，便于理解
- 图片使用腾讯云COS存储

## 提交信息规范

请使用清晰的提交信息，格式如下：

```
类型(范围): 简短描述

详细描述（可选）
```

类型包括：
- `feat`: 新功能
- `fix`: 修复bug
- `docs`: 文档更新
- `style`: 代码格式调整
- `refactor`: 代码重构
- `test`: 测试相关
- `chore`: 构建过程或辅助工具的变动

## 安全提醒

在贡献药材信息时，请确保：

1. 信息准确可靠，有科学依据
2. 包含安全提醒和注意事项
3. 强调需要专业指导
4. 避免误导性信息

## 联系方式

如果您有任何问题或建议，请通过以下方式联系我们：

- GitHub Issues: [项目Issues页面]
- 邮箱: [项目维护者邮箱]

感谢您的贡献！🌱 