# Shopify 商品上架 SOP · 十八的日常工作流

> 基于实习实际场景整理。目标是：少做重复劳动，把 AI 当同事用。

---

## 📋 完整流程（5步）

```
拍图/取图 → 图片处理 → 文案/描述 → SEO → 上架+检查
```

---

## 1️⃣ 图片处理

### 当前工具
- **即梦** — AI 图片处理

### 可补充的 AI 工具
| 工具 | 做什么 | 价格 |
|------|--------|------|
| **BatchShots** (batchshots.com) | 浏览器内批量编辑：去背景、压缩、调整大小、SEO 命名 | $19.99 一次性 |
| **Let's Enhance** | 电商图片放大、提升分辨率 | 有免费额度 |
| **DinoMark** (Shopify App) | 批量水印 + alt-text SEO 优化 | Shopify 内安装 |

### 标准操作
1. 原始图片去背景/裁剪（即梦 or BatchShots）
2. 统一尺寸（建议 2048×2048，Shopify 推荐）
3. 压缩为 WebP（减少 30-50% 体积，加载更快）
4. 文件命名含关键词：`产品名-颜色-材质.webp` 而不是 `IMG_001.webp`

### WebP 转换
```bash
# 单张
cwebp input.jpg -o output.webp -q 80

# 批量（在图片目录下）
for f in *.jpg; do cwebp "$f" -o "${f%.jpg}.webp" -q 80; done
```

---

## 2️⃣ 商品文案

### 用 AI 写描述
不用从头写。流程：
1. 给 AI 商品基本信息（名称、材质、尺寸、用途）
2. 让 AI 生成 3-5 个版本的英文描述
3. 选最好的，手动微调语气
4. 批量生成同类商品的模板

### 提示词模板
```
你是 Shopify 跨境电商文案。请为以下商品写英文产品描述：

商品名：[name]
材质：[material]
尺寸：[size]
用途：[use case]
目标用户：[target audience]
品牌语气：[casual/professional/luxury]

要求：
- 标题 60 字符以内，含主关键词
- 描述分 3 段：hook → features → benefits
- 列出 5 个 bullet points
- 含 SEO 关键词
- 自然不机械
```

### 工具推荐
- **Hypotenuse AI** — 批量生成、品牌语气一致（500K 用户）
- **Claude/Codex** — 你已经在用，继续用就行

---

## 3️⃣ SEO 基础

### 每个商品页面必填
| 字段 | 怎么做 |
|------|--------|
| **Title tag** | 产品名 + 核心关键词，< 60 字符 |
| **Meta description** | 1-2 句吸引点击的描述，< 155 字符 |
| **URL handle** | 简短含关键词：`/products/red-cotton-t-shirt` |
| **Alt text** | 每张图片写描述性文字（含关键词） |
| **H1** | 只用一次，放产品名 |

### SEO 检查清单
- [ ] 标题含主要搜索词
- [ ] 描述 300+ 词（Google 喜欢长内容）
- [ ] 图片 alt text 全部填写
- [ ] 产品分类页有文字描述（不是只有商品列表）
- [ ] 内部链接：相关产品互相推荐

---

## 4️⃣ 上架清单

上线前逐项检查：

- [ ] 图片 ≥ 3 张（主图 + 细节 + 场景）
- [ ] 所有图片已转 WebP + 有 alt text
- [ ] 商品标题 + 描述已 SEO 优化
- [ ] 价格 + 库存信息正确
- [ ] 变体（颜色/尺寸）全部配置
- [ ] 运费模板已关联
- [ ] 分类标签已打
- [ ] 手机端预览通过

---

## 5️⃣ 批量化技巧

**同类商品一次性处理：**
1. 收集所有图片 → 批量 WebP + 重命名
2. 用 AI 批量生成描述（Hypotenuse or Claude）
3. 用 Shopify bulk editor 统一改价格/标签
4. 最后逐个人工抽查质量

**节省时间的原则：**
- 不要一个一个做 → 一批一批做
- 不要让 AI 只生成一个 → 让它生成 3-5 个你挑
- 模板化：同类商品用同一个提示词，只改参数

---

## 🛠️ 工具速查

| 步骤 | 工具 | 替代方案 |
|------|------|---------|
| 图片处理 | 即梦 / BatchShots | GIMP + ImageMagick |
| 图片放大 | Let's Enhance | Topaz Gigapixel ($) |
| WebP 转换 | cwebp CLI | Squoosh (网页版) |
| 文案 | Claude / Hypotenuse AI | ChatGPT |
| SEO 检查 | Hypotenuse AI 内置 | Google Search Console |
| 批量水印 | DinoMark (Shopify App) | - |

---

## 📝 每日记录建议

每天结束时花 5 分钟记：
- 今天上了几个商品？
- 哪个步骤最花时间？
- 有没有可以明天批量处理的？

这样一周后就能看到哪些步骤可以优化。

---

> 这是 v1。根据实际使用反馈迭代。有什么不好用的告诉我。
