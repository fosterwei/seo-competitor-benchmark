# 从零实现美国英语美甲灵感内容站

## 1. 文档目标

本方案用于从零搭建一个面向美国全国、英语用户、以个人消费者为主的美甲灵感内容网站。目标不是复制 Nails for Confidence 的页面，而是借鉴其有效的搜索需求覆盖方式，同时补足原创性、图片授权、作者可信度、主题架构和可持续更新能力。

推荐的第一阶段产品形态是：

- 内容型网站，不做虚构的本地沙龙业务
- 以美甲设计灵感、颜色、甲型、季节和场景为核心主题
- 通过 Google Web、Google Images、Pinterest、Instagram 和品牌搜索获得流量
- 以邮件订阅、社交关注、品牌合作和未来商业化为主要转化
- 首发使用英文内容，技术架构保留未来多语言能力

## 2. 产品定位

### 2.1 目标用户

主要用户是美国英语女性个人消费者，包括：

- 正在寻找下一次美甲设计的用户
- 想在家 DIY 的初学者
- 需要给美甲师展示参考图的用户
- 按季节、颜色、甲型或场合寻找灵感的用户
- 通过 Pinterest、Instagram 或 Google Images 浏览图片的用户

### 2.2 核心承诺

每篇页面都要帮助用户更快回答至少一个问题：

- 我下一次应该做什么样的美甲？
- 这个设计适合我的甲型、长度和场合吗？
- 我能在家完成，还是需要专业美甲师？
- 我需要什么颜色、工具和时间？
- 还有哪些相似设计可以继续浏览？

### 2.3 不做什么

首版不应：

- 虚构门店地址、服务区域或 Google Business Profile
- 购买批量目录链接或垃圾外链
- 直接复制 Instagram、Pinterest 或其他网站图片
- 每年为相同季节主题无限创建近似 URL
- 用 AI 批量生成没有实用信息的薄文章
- 在没有专业审阅时发布医疗、安全或过敏结论
- 把内容博客伪装成电商或沙龙

## 3. MVP 范围

### 3.1 首发页面

最低可发布版本包含：

1. 首页
2. 5 个 Pillar 中心页：Nail Design Ideas、Nail Art & Techniques、Nail Colors、Nail Shapes & Lengths、Seasonal & Occasion Nails
3. 3 个首批 Cluster 页：Short Nails、French Tip Nails、Summer Nails
4. 12 篇长列表文章
5. About 页面
6. 作者 Profile 页面
7. Contact 页面
8. Privacy Policy、Terms 和 Image Rights 页面
9. 404 页面
10. XML Sitemap、robots.txt 和 RSS/Atom Feed

首发建议准备 30-50 张自有或明确授权图片，避免上线后页面只有外部图片嵌入。

### 3.2 MVP 的成功标准

上线后 90 天内，以以下指标判断是否值得扩展：

- 主要页面全部可抓取、可索引且无严重 canonical 错误
- 文章模板在移动端加载稳定，没有明显布局跳动
- 每篇文章有清晰主搜索意图和至少 3 个相关内链
- 图片有授权记录、描述性文件名和准确 alt
- Search Console 能看到展示次数和长尾查询增长
- 至少 5 个页面获得自然展示或图片展示
- 邮件订阅或社交关注有可测量的增长

## 4. 推荐技术架构

### 4.1 推荐方案：WordPress + 轻量主题

对于需要每周持续发布内容的个人或小团队，推荐：

- CMS：WordPress
- 主题：自定义轻量主题，或在轻量基础主题上扩展
- SEO：选择一个主 SEO 插件，不要叠加多个 SEO 插件
- 图片：WordPress Media Library + WebP/AVIF 转换
- CDN：Cloudflare 或主机自带 CDN
- 托管：支持对象缓存、自动备份、PHP 版本更新和 HTTPS 的 WordPress 托管
- 分析：Google Search Console、GA4、Bing Webmaster Tools
- 版本控制：主题、模板和自定义插件进入 Git；文章与媒体留在 CMS

选择 WordPress 的原因是作者、分类、文章、媒体、站点地图和编辑流程成熟，适合内容团队。若团队已经熟悉 React/TypeScript，也可以使用 Astro 或 Next.js + Headless CMS，但必须自己解决预览、作者、媒体、重定向、站点地图和编辑协作。

### 4.2 目录建议

自定义主题或前端项目至少保持以下边界：

```text
site/
├── app-or-theme/
│   ├── templates/
│   │   ├── home
│   │   ├── archive
│   │   ├── single-post
│   │   ├── author
│   │   └── page
│   ├── components/
│   │   ├── article-card
│   │   ├── topic-nav
│   │   ├── related-posts
│   │   ├── breadcrumbs
│   │   └── newsletter-form
│   ├── assets/
│   │   ├── css
│   │   └── js
│   └── functions/
├── content/
│   ├── briefs
│   ├── editorial-calendar
│   └── image-rights
└── docs/
```

### 4.3 环境和发布

至少准备：

- 本地开发环境
- staging 环境
- production 环境
- 数据库和媒体自动备份
- HTTPS、强密码、双因素认证
- 服务器和插件更新计划
- 发布前检查清单
- 回滚或恢复流程

## 5. 信息架构

### 5.1 推荐 URL 结构

使用简短、稳定、可读的英文 URL：

```text
/
 /nail-art/
 /nail-colors/
 /seasonal-nails/
 /pedicure/
 /short-nails/
 /french-tip-nails/
 /almond-nails/
 /summer-nails/
 /posts/short-summer-french-tip-nails/
 /author/maria/
 /about/
```

建议将文章 URL 控制在主题词范围内，不把年份写进永久 URL，除非页面只服务一次性事件。季节性主题优先更新长期 URL，而不是每年创建新的相似 URL。

### 5.2 三层主题模型

```text
Seasonal Nails
├── Summer Nails
│   ├── Summer French Tip Nails
│   ├── Beach Nails
│   └── Short Summer Nails
├── Spring Nails
└── Christmas Nails

Nail Colors
├── Red Nails
├── Pink Nails
├── Blue Nails
└── Chrome Nails
```

每个中心页负责解释主题、链接子主题和展示精选文章；文章负责覆盖更具体的长尾意图。不要让标签页、作者页和搜索结果页大量占用索引预算。

### 5.3 导航设计

全局导航保持 5-6 个主入口；将 Latest、About 和搜索作为辅助入口，将 Pedicure 作为独立垂直入口而不是与颜色、形状平行的无限筛选器：

- Latest
- Nail Design Ideas
- Nail Art
- Nail Colors
- Nail Shapes
- Seasonal Nails
- Pedicure
- About

首页应同时提供：

- 最新内容
- 按主题浏览
- 按季节浏览
- 按甲型浏览
- 邮件订阅
- 作者和品牌入口

### 5.4 完整站点地图

以下结构适合作为第一版产品和后续扩展的基准。括号内为页面的主要 SEO 或转化职责。

```text
/
├── /latest/                         # 最新文章流
├── /nail-art/                       # Nail Art 主题中心
│   ├── /french-tip-nails/           # 技法/风格中心
│   ├── /aura-nails/
│   ├── /chrome-nails/
│   ├── /marble-nails/
│   └── /simple-nail-art/
├── /nail-colors/                    # 颜色主题中心
│   ├── /red-nails/
│   ├── /pink-nails/
│   ├── /blue-nails/
│   ├── /green-nails/
│   ├── /black-nails/
│   └── /nude-nails/
├── /seasonal-nails/                 # 季节主题中心
│   ├── /spring-nails/
│   ├── /summer-nails/
│   ├── /fall-nails/
│   ├── /winter-nails/
│   └── /christmas-nails/
├── /nail-shapes/                    # 甲型中心
│   ├── /short-nails/
│   ├── /almond-nails/
│   ├── /coffin-nails/
│   ├── /square-nails/
│   └── /stiletto-nails/
├── /occasions/                      # 场景中心
│   ├── /vacation-nails/
│   ├── /wedding-nails/
│   ├── /prom-nails/
│   └── /office-nails/
├── /pedicure/                       # 脚部护理和搭配主题
├── /posts/                          # 文章 URL 命名空间
│   └── /short-summer-french-tip-nails/
├── /author/                         # 作者实体
│   └── /maria/
├── /about/
├── /contact/
├── /image-rights/
├── /privacy-policy/
├── /terms/
├── /search/                         # 站内搜索，默认 noindex
└── /404/
```

不要一开始创建所有目录。只有当一个主题至少有 3-5 篇高质量文章、明确的搜索意图和独立的页面简介时，才把它升级为可索引中心页。

### 5.5 页面职责和模块契约

#### 首页 `/`

目标：说明网站是什么、展示最新内容、把用户送到主题中心。

模块顺序建议：

1. Header、品牌名、主导航和搜索
2. 简短 H1 和一句价值说明
3. Featured article 或 Featured collection
4. Browse by topic：4-6 个主题中心
5. Latest posts：6-12 篇文章
6. Browse by season/color/shape
7. Newsletter signup
8. About the creator
9. Footer、隐私和版权链接

首页不要使用大段营销文案或无法点击的装饰卡片。首屏应立即呈现品牌、真实美甲图片和可继续浏览的内容。

#### 主题中心页 `/nail-art/`、`/summer-nails/`

目标：解释主题、承接宽泛搜索、分发权重到子主题和文章。

必须包含：

- 唯一 H1 和 100-250 字简介
- 主题相关的主图
- 子主题导航
- 8-24 篇精选文章
- 按最新、热门或适用场景的排序方式
- 面包屑
- 相关中心页链接
- 主题 FAQ（有真实问题时）

中心页不应只是文章卡片列表。需要明确说明用户在这里能找到哪些设计、如何筛选，以及与相邻主题的区别。

#### 文章页 `/posts/{slug}/`

目标：完整解决一个具体搜索意图，并把用户引导到下一个相关主题。

模块顺序建议：

1. Breadcrumbs
2. Category、H1、author、published/modified date
3. Featured image
4. Intro 和目录
5. Design list，每个条目使用 H2/H3
6. 实用选择建议或 DIY 说明
7. FAQ（如果能降低用户决策成本）
8. Related posts
9. Newsletter CTA
10. Author bio 和版权/来源说明

文章模板必须支持 3-50 个设计条目，不应因条目数量改变布局或破坏目录。

#### 作者页 `/author/{slug}/`

目标：建立作者实体、聚合文章、说明经验边界。

包含头像、简介、擅长主题、内容审核方式、代表文章和社交链接。作者页可以被索引，但内容不足时应暂缓发布或补齐实体信息。

#### About、Contact、Image Rights

About 解释品牌、作者和编辑原则；Contact 提供合作和纠错入口；Image Rights 解释图片来源、授权和侵权联系流程。这三页共同支撑信任和品牌实体，不是装饰页面。

### 5.6 内容类型和数据关系

建议在 CMS 中定义以下内容类型：

| 内容类型 | 关键字段 | 关联对象 | 默认索引 |
|---|---|---|---|
| Post | 标题、摘要、设计条目、主图、作者、日期 | 主题、颜色、甲型、场景 | 是 |
| Topic hub | 简介、主图、精选文章、子主题 | Post、Topic hub | 是 |
| Author | 姓名、头像、简介、社交链接 | Post | 是，需完整 |
| Design entry | 名称、颜色、甲型、难度、图片、授权 | Post | 否，嵌入文章 |
| Image asset | 文件、alt、来源、许可、摄影者 | Post、Design entry | 通过图片出现 |
| Redirect | 旧 URL、新 URL、原因 | Post、Topic hub | 否 |

文章可以关联多个主题，但必须指定一个 primary topic。Primary topic 用于 breadcrumb、主内链和页面上下文，避免同一文章被多个分类模板重复渲染。

### 5.7 URL、面包屑和规范化规则

- 所有公开 URL 使用小写、连字符和尾部斜杠策略的一致版本。
- 文章使用 `/posts/{descriptive-slug}/`；中心页使用短主题 slug。
- 不把分类层级硬编码进文章 URL，避免文章换主题时产生大规模迁移。
- 删除或合并页面时保留 301 映射，不直接返回软 404。
- URL 参数用于站内筛选时默认 noindex；如果某个筛选组合有独立搜索价值，再建立静态中心页。
- Breadcrumb 必须与用户可见导航和 canonical URL 一致。

### 5.8 内链图和孤立页规则

每个可索引文章至少具备以下入链：

```text
Home
  -> Primary topic hub
    -> Article
      -> Related article
      -> Secondary topic hub
```

发布前检查：

- 新文章从至少一个中心页或专题页可达
- 文章正文至少链接一个上级主题和两个相关文章
- 中心页链接最重要的文章，而不是只显示最新文章
- 季节、颜色、甲型和场景之间存在交叉链接
- 没有只能通过站内搜索才能找到的孤立可索引页

### 5.9 索引分层

| 页面 | 可索引 | Sitemap | 说明 |
|---|---|---|---|
| 首页 | 是 | 是 | 品牌和主题入口 |
| 主题中心 | 是 | 是 | 有独立简介和足够内容时 |
| 文章页 | 是 | 是 | 规范 URL |
| 作者页 | 视完整度 | 是/否 | 内容足够时建立作者实体 |
| 标签页 | 通常否 | 否 | 避免薄内容和重复聚合 |
| 站内搜索 | 否 | 否 | 防止参数 URL 膨胀 |
| 分页 | 视实现 | 否 | 保持可爬取，但不必全部进 sitemap |
| 草稿、预览、测试页 | 否 | 否 | 登录保护或 noindex |

### 5.10 设计和开发验收标准

设计验收：

- 桌面和移动端都有稳定的 Header、导航和搜索入口
- 首页首屏同时出现品牌、真实主图和下一段内容入口
- 文章条目有稳定尺寸，图片加载不会推动文字跳动
- 卡片不嵌套卡片，主题区块使用完整页面带或清晰网格
- 文本、按钮和图片在小屏幕不重叠、不溢出
- 颜色和字体对比度满足可读性要求

开发验收：

- 每种模板有唯一 title、H1、canonical 和结构化数据
- 主题、作者、文章和图片字段可在 CMS 中独立维护
- 文章条目数量变化不会破坏 CSS Grid 或目录
- 相关内容组件按 primary/secondary topic 工作，不依赖手工硬编码
- 删除、合并和改 slug 都能创建 301
- staging 不会出现在生产 sitemap
- 发布后可以在 Search Console 检查 URL 和富结果

## 6. 关键词、实体与 Topical Authority 架构

### 6.1 研究口径和证据边界

本项目的关键词架构应以美国英语 SERP 的实际重叠为最终依据，而不是只按词面相似度分组。当前公开调研能确认的信号包括：

- 用户和竞品内容反复围绕 `nail ideas`、`nail designs`、`nail art`、`summer nails`、`French tip nails`、`short nails`、`almond nails`、`coffin nails`、颜色和场景词组织内容。
- 近期公开搜索结果显示，`short summer nails`、`summer French tip nails` 和 `simple summer nails` 会形成高度相邻但不完全相同的页面意图；短甲、季节和 French tip 更适合作为交叉实体，而不是全部变成同级栏目。可参考 [Short Summer French Tip Nails](https://parisfy.com/short-summer-french-tip-nails/) 和 [Simple Short Summer Nails](https://ideasnail.com/simple-short-summer-nails/)。
- 趋势媒体会把颜色、质感、技法和季节组合成新的设计实体，例如 chrome、aura、micro-French、metallic、butter yellow 等；这些词适合进入 Cluster 或 Post，只有稳定形成独立意图后才升级为 Pillar。可参考 [夏末 French tip 趋势](https://www.whowhatwear.com/beauty/nails/august-french-tip-nail-ideas-2026) 和 [金属质感美甲趋势](https://www.marieclaire.com/beauty/nails/best-metallic-nails/)。

没有 DataForSEO、Ahrefs、GSC 或 Google Ads Keyword Planner 数据时，不要填写虚构搜索量、难度或流量预测。先使用“候选主题”，上线后通过 Search Console 展示词、点击和 SERP 重叠复核，再决定扩展或合并。

### 6.2 实体模型

网站应围绕以下实体建立统一词汇，而不是围绕任意关键词堆页面：

| 实体 | 说明 | 典型属性 | 关系 |
|---|---|---|---|
| NailDesign | 一套具体美甲设计 | name、image、palette、style | hasColor、usesTechnique、fitsShape |
| NailArtStyle | 视觉风格或技法 | French tip、aura、chrome、marble | appliedToDesign |
| NailColor | 颜色或色系 | red、pink、blue、nude、green | appearsInDesign |
| Finish | 表面质感 | glossy、matte、glitter、metallic、velvet | modifiesDesign |
| NailShape | 甲型 | almond、coffin、square、oval、stiletto | fitsLength |
| NailLength | 长度 | short、medium、long | constrainsTechnique |
| Season | 时间/季节 | spring、summer、fall、winter、Christmas | inspiresDesign |
| Occasion | 使用场景 | vacation、wedding、prom、office、date night | suitableForDesign |
| SkillLevel | 执行难度 | beginner、intermediate、professional | affectsHowTo |
| ProductTool | 工具或产品类别 | gel、polish、brush、sticker、chrome powder | usedForHowTo |
| Creator | 作者或被授权创作者 | name、profile、rights | createdOrContributed |
| ManicurePedicure | 手部或脚部内容 | fingernail、toenail、matching set | relatedToDesign |

页面标题可以包含多个实体，但每个可索引页面必须指定一个 primary entity 和一个 dominant intent。例如：

- `25 Short Summer French Tip Nails`：primary entity = NailDesign；dominant intent = visual inspiration/list
- `What Nail Shape Is Best for Short Nails?`：primary entity = NailShape；dominant intent = informational guide
- `Chrome Nail Designs`：primary entity = Finish/Technique；dominant intent = inspiration hub
- `Matching Fingernail and Toenail Designs`：primary entity = ManicurePedicure；dominant intent = inspiration/list

### 6.3 推荐的 Pillar 层级

首版只建立 5 个可索引 Pillar，避免分类数量过多：

| Pillar | 核心主题 | 主要实体 | 适合承接的词群 |
|---|---|---|---|
| Nail Design Ideas | 全站核心入口 | NailDesign | nail ideas、nail designs、manicure ideas、nail inspiration |
| Nail Art & Techniques | 风格和技法 | NailArtStyle、Finish | nail art、French tip、aura、chrome、marble、glitter |
| Nail Colors | 颜色和质感 | NailColor、Finish | red nails、pink nails、blue nails、nude nails、metallic nails |
| Nail Shapes & Lengths | 形状和长度 | NailShape、NailLength | short nails、almond nails、coffin nails、square nails |
| Seasonal & Occasion Nails | 时间和场景 | Season、Occasion | summer nails、Christmas nails、vacation nails、wedding nails |

`Pedicure` 可以作为独立导航入口，但在首版不建议把它和手部美甲完全混入同一个分类树。它应作为一个业务/内容垂直主题，内部连接到 `Matching Mani-Pedi`、`Toe Nail Designs` 和季节场景页面。

### 6.4 Pillar → Cluster → Post 规划

以下是首批可执行的候选架构。它是内容规划起点，不是最终关键词排名承诺。

#### Pillar A：Nail Design Ideas

Cluster：

- `Simple Nail Ideas`
- `Cute Nail Ideas`
- `Classy Nail Ideas`
- `Nail Ideas for Beginners`

Post 示例：

- `25 Simple Nail Designs That Look Expensive`
- `30 Cute Nail Ideas for Short Nails`
- `20 Classy Nail Designs for Every Occasion`
- `Easy Nail Art Ideas You Can Do at Home`

页面职责：覆盖最宽的灵感需求，链接到所有其他 Pillar；不要让它与 `Nail Art & Techniques` 的具体技法页重复。

#### Pillar B：Nail Art & Techniques

Cluster：

- `French Tip Nails`
- `Aura Nails`
- `Chrome and Metallic Nails`
- `Marble, Floral, and Abstract Nails`

Post 示例：

- `25 Colored French Tip Nail Designs`
- `Short French Tip Nails for Everyday Wear`
- `Aura Nail Designs in Pink, Blue, and Neutral Tones`
- `Chrome Nail Ideas from Minimal to Statement`
- `Simple Marble Nail Art for Beginners`

页面职责：解释技法和视觉风格；同一技法的颜色或季节变化进入 Post，不再重复建立多个同义 Pillar。

#### Pillar C：Nail Colors

Cluster：

- `Red and Pink Nails`
- `Blue, Green, and Yellow Nails`
- `Black, White, and Nude Nails`
- `Chrome, Glitter, and Metallic Finishes`

Post 示例：

- `25 Red Nail Designs from Classic to Modern`
- `Pink Nail Ideas for Short and Almond Nails`
- `Blue Summer Nail Designs to Save`
- `Nude Nail Ideas with French Tips and Chrome`
- `Glitter Nail Designs for Day-to-Night Looks`

页面职责：围绕颜色实体组织设计，不为每一种颜色和每一种季节组合自动建页。只有 SERP 意图明显独立、内容足够深时才建立静态页面。

#### Pillar D：Nail Shapes & Lengths

Cluster：

- `Short Nails`
- `Almond Nails`
- `Coffin/Ballerina Nails`
- `Square, Oval, and Stiletto Nails`

Post 示例：

- `Short Nail Designs That Do Not Need Length`
- `Almond Nail Ideas for Every Season`
- `Coffin Nail Designs from Simple to Bold`
- `Best Nail Shapes for Short Nail Beds`
- `Short vs Almond vs Coffin Nails: Choosing a Shape`

页面职责：解决选择和适配问题。形状页应提供长度、甲床、维护、场景和设计限制等实用信息，不能只做图片清单。

#### Pillar E：Seasonal & Occasion Nails

Cluster：

- `Spring Nails`
- `Summer Nails`
- `Fall and Winter Nails`
- `Holiday and Event Nails`

Post 示例：

- `25 Summer Nail Designs from Simple to Bold`
- `Short Summer French Tip Nails`
- `Spring Floral Nail Designs`
- `Fall Nail Colors and Designs`
- `Christmas Nail Designs for Short Nails`
- `Vacation Nail Ideas for Beach Trips`
- `Wedding Nail Ideas for Brides and Guests`

页面职责：承接季节和场景需求，并回链颜色、形状和技法实体。季节页采用长期 URL，按年份刷新，不重复生成 `/summer-nails-2027/` 这类近似页面。

### 6.5 关键词到页面的分配规则

#### Pillar page

适合：宽泛实体词、总览型意图、需要继续分流的查询。

- 目标长度：约 2,500-4,000 字
- 内容：实体定义、子主题、筛选路径、精选文章、FAQ
- 主关键词：一个宽泛实体主题
- 内链：链接所有核心 Cluster，并从所有 Cluster 回链

#### Cluster page

适合：一个稳定的子主题，能承接多篇文章且有独立解释价值。

- 目标长度：约 1,800-2,800 字
- 内容：子主题简介、设计分类、选择建议、精选 Posts
- 主关键词：一个子主题/风格/颜色/形状
- 升级条件：至少 3-5 篇可互相支持的 Post，且 SERP 意图不等同于上级 Pillar

#### Post page

适合：单一长尾问题、列表、教程、比较或具体场景。

- 灵感列表：1,200-1,800 字，设计条目必须有实用描述
- 教程/解释：1,500-2,500 字，必须有步骤、限制和适用人群
- 比较页：1,800-2,500 字，必须有明确决策标准
- 每篇只设置一个 primary keyword，其他词作为自然变体

### 6.6 SERP 重叠和蚕食判定

对每组候选词执行实际 SERP 重叠检查：

| 共同 Top 10 结果 | 判定 | 页面动作 |
|---:|---|---|
| 7-10 | 同一意图 | 合并为一个页面，覆盖多个变体 |
| 4-6 | 同一主题集群 | 分成 Pillar/Cluster 或同集群 Posts |
| 2-3 | 相邻主题 | 分开建页，并安排交叉内链 |
| 0-1 | 意图不同 | 分到不同 Pillar，或暂不创建 |

执行顺序：先按信息型、灵感列表型、比较型、教程型分组，再对同组候选词比较 Top 10 URL。不要只因两个词都含有 `nails` 就把它们合并，也不要只因词面不同就强行拆页。

上线前必须检查：

- 每个 Post 的 primary keyword 唯一
- 同一实体和同一意图没有多个 URL
- 组合词页有新增价值，而不是把 Pillar 标题换个顺序
- 颜色、季节、形状的交叉页有独立用户问题
- 没有因为标签、筛选参数和作者归档产生重复页面

### 6.7 Topical Authority 的建设顺序

不要从大量 Post 开始。推荐顺序：

1. 先完成 `Nail Design Ideas` 核心 Pillar
2. 建立 `Nail Art & Techniques` 和 `Nail Shapes & Lengths` 两个支撑 Pillar
3. 每个 Pillar 发布 3-4 个 Cluster 页面
4. 每个 Cluster 先发布 3 篇高质量 Post
5. 补齐颜色、季节和场景交叉内容
6. 根据 Search Console 的新查询和实际 SERP 重叠扩展
7. 合并没有独立意图或没有获得展示的重复页面

一个主题达到 topical authority 的最低内部标准：

- 有 1 个清晰 Pillar
- 有至少 3 个有独立意图的 Cluster
- 每个 Cluster 至少 3 篇实质不同的 Post
- 所有 Post 都有 Pillar 入链和回链
- Post 之间有 2-3 个正文上下文内链
- 页面覆盖定义、选择、做法、场景和限制，而不只是图片
- 作者、图片权利和更新记录可追溯

### 6.8 推荐首发 36 页

首发不需要覆盖整个词库，先建立一个可验证的主题图：

- 5 个 Pillar pages
- 12 个 Cluster pages（每个 Pillar 2-3 个）
- 19 个 Post pages

建议首发 Posts：

1. 25 Simple Nail Designs That Look Expensive
2. 30 Cute Nail Ideas for Short Nails
3. Easy Nail Art Ideas You Can Do at Home
4. 25 Colored French Tip Nail Designs
5. Short French Tip Nails for Everyday Wear
6. Aura Nail Designs in Pink, Blue, and Neutral Tones
7. Chrome Nail Ideas from Minimal to Statement
8. 25 Red Nail Designs from Classic to Modern
9. Pink Nail Ideas for Short and Almond Nails
10. Blue Summer Nail Designs to Save
11. Nude Nail Ideas with French Tips and Chrome
12. Glitter Nail Designs for Day-to-Night Looks
13. Short Nail Designs That Do Not Need Length
14. Almond Nail Ideas for Every Season
15. Coffin Nail Designs from Simple to Bold
16. Best Nail Shapes for Short Nail Beds
17. 25 Summer Nail Designs from Simple to Bold
18. Short Summer French Tip Nails
19. Spring Floral Nail Designs

这些页面发布前仍需进行 SERP 重叠、关键词难度和内容差异验证。若两个候选词返回高度相同的页面，应合并，而不是为了达到页数目标拆成两篇。

### 6.9 内链矩阵

每个 Cluster 采用双向链接：

| 来源 | 目标 | 必须性 | 锚文本示例 |
|---|---|---|---|
| Pillar | Cluster | 必须 | `French tip nail ideas` |
| Cluster | Pillar | 必须 | `nail design ideas` |
| Cluster | Post | 必须 | `short summer French tip nails` |
| Post | Cluster | 必须 | `summer French nails` |
| Post | 同 Cluster Post | 2-3 个 | `simple French tip designs` |
| Post | 相邻 Cluster | 0-1 个 | `almond nail ideas` |

所有 Post 应在正文中至少获得 3 个入链，并且在两次点击内可从首页或核心 Pillar 到达。不要只依赖侧边栏、标签或“最新文章”模块。

### 6.10 关键词研究的持续更新机制

每月从 Search Console 导出：

- 有展示但没有点击的新查询
- 多个 URL 同时获得展示的查询
- 页面实际排名词与原始 primary keyword 的差异
- 图片搜索带来的查询
- 季节性词的同比变化

每季度执行一次 SERP 重叠复核：

1. 更新候选关键词表
2. 合并重复意图
3. 新增具有独立实体或场景的问题
4. 修改 Pillar/Cluster 的内部链接
5. 对长期没有展示的薄页进行合并、重写或 noindex

不要用固定的“每月发布多少篇”衡量权威建设。更重要的指标是实体覆盖、意图覆盖、内部链接完整度、自然查询增长和页面之间的重复率。

## 7. 内容模型

### 7.1 文章字段

每篇文章在 CMS 中至少有：

- Title
- Slug
- Primary topic
- Secondary topics
- Search intent
- Meta title
- Meta description
- H1
- Intro
- Table of contents
- Design entries
- Author
- Date published
- Date modified
- Featured image
- Image rights record
- Related posts
- FAQ, if genuinely useful
- Editorial status
- Refresh date

### 7.2 设计条目字段

列表文章中的每个设计不要只有图片和一句形容词。至少写出：

- Design name
- Color palette
- Nail shape and length
- Occasion or audience
- DIY difficulty
- Approximate time
- Tools or polish types
- What makes the design distinctive
- Image source and permission status

### 7.3 内容矩阵

用变量组合形成可扩展主题：

| 变量 | 示例 |
|---|---|
| 季节 | spring, summer, fall, Christmas |
| 颜色 | red, pink, blue, chrome, nude |
| 风格 | classy, simple, minimalist, glitter |
| 甲型 | almond, coffin, short, square |
| 场景 | vacation, wedding, prom, office |
| 技法 | French tip, aura, chrome, marble |

每个新选题必须说明：

1. 主搜索意图是什么
2. 与现有 URL 的差异是什么
3. 用户会得到什么新信息
4. 是否值得新建 URL，还是应该更新中心页
5. 需要哪些原创或授权图片

### 7.4 文章模板

```text
H1: 25 Short Summer Nail Ideas for 2026

导语：说明用户会找到什么，适合什么人

目录

H2: Simple Short Summer Nails
H3: Design 1
- 图片
- 颜色、甲型、场景
- 难度和 DIY 说明

H2: Summer French Tips
H3: Design 2
...

H2: How to Choose the Right Summer Nail Design
FAQ（仅回答页面真实覆盖的问题）

Related:
- Summer Nail Colors
- Short French Tip Nails
- Vacation Nail Ideas
```

### 7.5 内容质量标准

每篇文章发布前必须通过：

- 主关键词在标题、H1、导语和自然内链中有合理体现
- 不用同义词机械堆叠
- 每个设计条目包含可执行信息
- 文章有明确作者
- 文章中没有无法证明的安全或专业断言
- 重要内容有更新日期
- 内链至少包含一个主题中心、两个相关页面
- 图片版权状态为 approved
- 页面首屏能快速展示内容主题

## 8. 图片和版权流程

### 8.1 图片来源优先级

按优先级使用：

1. 自己拍摄的原创图片
2. 获得书面授权的创作者图片
3. 有明确商业许可的图库或素材
4. 用户投稿并签署授权协议
5. 仅作为灵感来源的外部图片，不直接复制到站内

“标注 Instagram 账号”不等于获得使用权。每张非原创图片都需要记录：

- 原作者
- 来源 URL
- 授权日期
- 授权范围
- 是否允许裁剪、压缩、商业使用
- 署名方式
- 证据文件位置
- 撤回或替换状态

### 8.2 图片技术标准

- 文件名描述主题，例如 `short-pink-french-tip-nails.webp`
- alt 描述图片实际内容，不堆关键词
- 使用 WebP 或 AVIF，同时保留合理回退格式
- 生成响应式尺寸
- 图片元素预留宽高，避免 CLS
- 首屏主图不要无条件 lazy-load
- 非首屏图片使用 lazy-loading
- 生成 Open Graph 图片
- 定期清理未使用的大图和重复尺寸

Google 图片优化强调可抓取图片、描述性文件名、准确 alt、相关页面上下文和合理的 `og:image`。这些是上线检查项，不是可选装饰。

## 9. SEO 实现

### 9.1 基础技术 SEO

上线前检查：

- HTTPS 全站启用
- HTTP 自动跳转 HTTPS
- 一个规范主域名
- 每个可索引页面只有一个 canonical
- robots.txt 不阻塞文章、分类和图片
- XML Sitemap 只包含规范、可索引 URL
- 404 返回真实 404 状态
- 分页和标签策略明确
- 搜索结果页、测试页、草稿页 noindex
- 移动端可用
- 页面有唯一 title、meta description 和 H1
- 页面可在不依赖用户点击的情况下展示主要内容
- 站点支持 RSS 或 Atom Feed

### 9.2 Title 和 Meta 模板

Title 模板要具体，不要所有页面重复品牌名：

```text
文章：{Primary Topic}: {Specific Benefit} | {Brand}
分类：{Category Name} Nail Ideas and Inspiration | {Brand}
中心页：{Topic} Nail Ideas, Colors, and Designs | {Brand}
作者：{Author Name} | {Brand}
```

Meta description 说明内容范围和用户收益，不承诺无法证明的结果。Google 会综合 title、H1、页面文本和外部锚文本生成结果标题，因此页面视觉标题必须和 HTML title 语义一致。

### 9.3 结构化数据

推荐：

- 首页：WebSite、Organization
- 文章：Article 或 BlogPosting
- 层级：BreadcrumbList
- 作者：Person/ProfilePage
- 图片：必要时使用 ImageObject

不要添加：

- 页面没有展示的评分
- 虚假的评论
- 不存在的门店地址
- 隐藏的 FAQ
- 与正文不一致的产品或服务

使用 Rich Results Test 和 Schema Markup Validator 验证。结构化数据只能让页面有资格获得更丰富展示，不能保证 Google 一定显示富结果。

### 9.4 内链规则

每篇文章至少链接到：

- 一个上级主题中心页
- 两篇同主题或同季节文章
- 一个不同维度页面，例如颜色或甲型
- 作者或 About 页面（有实际帮助时）

锚文本描述目标页面，例如 `short summer nail ideas`，不要大量使用 `read more`。中心页要链接重要文章，重要文章也要回链中心页。

### 9.5 季节页管理

推荐长期 URL：

```text
/summer-nails/
/spring-nails/
/christmas-nails/
```

每年：

- 更新设计和导语
- 更新 dateModified
- 保留已获得链接的 URL
- 合并内容重叠的页面
- 301 重定向废弃 URL
- 更新首页和中心页的展示顺序

## 10. 作者、信任和品牌

### 10.1 作者实体

作者页应包含：

- 真实姓名或稳定使用的创作者名
- 头像
- 个人经历
- 擅长主题
- 内容审核或测试方式
- 代表文章
- 社交链接
- 联系方式

如果作者不是持证美甲师，应明确写“美甲爱好者/内容创作者”，不要暗示专业资质。涉及护理、安全、过敏和感染的问题，应引用权威来源或邀请专业人士审阅。

### 10.2 About 页面

About 页面回答：

- 为什么建立网站
- 谁在维护内容
- 内容如何选题和验证
- 图片如何获得
- 如何联系
- 商业合作如何披露

透明说明不是弱点；没有证据的专业包装才是风险。

### 10.3 社交分发

为每篇文章制作：

- 3-5 张 Pinterest 竖图
- 1 个 Instagram carousel
- 1 个短视频或 slideshow
- 1 条邮件摘要
- 1 个可复用的创作者署名卡

社交平台的主要价值是传播、品牌搜索、访问和自然链接，不要把关注者数量直接当作 Google 排名指标。

## 11. 本地 SEO边界

如果网站没有真实的门店或服务区域：

- 不创建虚构的 Google Business Profile
- 不批量创建城市页面
- 不购买本地目录链接
- 不在 Schema 中添加虚构 LocalBusiness
- 不把全国内容站写成“附近美甲店”

未来如果出现真实工作室：

- 使用真实名称、地址、电话和营业时间
- 保持网站、GBP 和引用站点 NAP 一致
- 上传真实环境和作品照片
- 及时回复评论
- 只创建有独立服务价值的地点页

Google 本地结果主要考虑相关性、距离和知名度，因此本地优化不能替代真实业务实体。

## 12. 分析和监控

### 12.1 必装工具

- Google Search Console
- Google Analytics 4
- Bing Webmaster Tools
- Bing URL Submission/IndexNow（适用时）
- PageSpeed Insights 或 Lighthouse
- Rich Results Test
- Schema Markup Validator
- 图片压缩和版权记录工具
- 邮件平台及 UTM 追踪

### 12.2 事件设计

GA4 至少记录：

- page_view
- scroll_50、scroll_90
- click_related_post
- click_category
- newsletter_view
- newsletter_signup
- outbound_creator_click
- social_share
- image_gallery_interaction

### 12.3 每周检查

- 新页面是否被发现
- Search Console 新查询和页面
- 404、重定向和 sitemap 错误
- 图片加载和移动端布局
- 邮件订阅转化
- 主要社交内容的点击和保存
- 是否出现重复或近似选题

### 12.4 每月检查

- 页面按主题的展示、点击和 CTR
- 有展示但低点击的 title/meta
- 有点击但低参与度的页面
- 新旧季节页的表现
- 内链覆盖和孤立页面
- 图片授权状态
- 外部链接和品牌提及
- 需要合并、更新或删除的页面

## 13. 发布流程

### 13.1 单篇文章流程

1. 选题去重
2. 定义主搜索意图
3. 建立内容 brief
4. 确定图片和授权
5. 撰写初稿
6. 添加内链和结构化信息
7. 编辑事实、语气和可读性
8. 检查 title、H1、meta、slug、canonical
9. 检查移动端和图片尺寸
10. 发布到 staging
11. 运行检查清单
12. 发布 production
13. 请求抓取并加入分发日历
14. 30-60 天后根据数据更新

### 13.2 发布前检查表

- [ ] URL 唯一且短
- [ ] Title 与 H1 清晰一致
- [ ] Meta description 具体
- [ ] 正文解决明确问题
- [ ] 图片全部有授权记录
- [ ] alt 文本准确
- [ ] 图片有宽高和合理格式
- [ ] Article/Breadcrumb Schema 已验证
- [ ] canonical 正确
- [ ] 至少 3 个相关内链
- [ ] 作者信息存在
- [ ] 页面移动端无溢出和遮挡
- [ ] 404、sitemap、robots 无新错误
- [ ] 文章已加入社交和邮件分发

## 14. 30/60/90 天路线图

### 第 1-30 天：打基础

- 定义品牌、受众和编辑规范
- 购买域名和稳定托管
- 完成 WordPress、主题和安全配置
- 建立 4 个中心页
- 创建 About、Author、Contact、Privacy 和 Image Rights
- 发布 12 篇高质量核心文章
- 配置 HTTPS、canonical、sitemap、robots、Schema、GSC 和 GA4
- 建立图片授权表
- 设置备份和 staging

### 第 31-60 天：扩展主题

- 发布 12-18 篇长尾文章
- 加强中心页与文章之间的双向内链
- 完成 Short Nails、French Tips、Almond Nails 等专题
- 制作 Pinterest 和 Instagram 分发模板
- 联系获得授权的创作者开展合作
- 优化低 CTR 页面标题和描述
- 检查图片尺寸、LCP 和 CLS
- 开始收集邮件订阅

### 第 61-90 天：根据数据增长

- 依据 Search Console 查询扩展主题
- 合并重复季节页
- 更新已有文章而不是无条件新建近似 URL
- 发布一份原创趋势报告或设计合集
- 建立品牌合作和自然链接计划
- 测试 newsletter、affiliate 或商业合作入口
- 输出第一次内容和 SEO 月报
- 决定下一季度重点是内容规模、图片原创、品牌合作还是产品化

## 15. 商业化顺序

在有稳定自然流量和清晰受众之前，不要堆叠广告。建议顺序：

1. 邮件订阅和品牌自有受众
2. 合规的美甲工具、护理产品 affiliate
3. 品牌赞助内容，并清晰披露
4. 原创数字产品，例如设计清单或教程
5. 创作者合作和内容授权
6. 线下课程、服务或电商（只有真实业务成立时）

每种商业化都要维护编辑独立性，不能为了佣金改变真实评价。

## 16. 最终实施原则

优先建设可以长期积累的资产：

- 稳定的主题中心页
- 真实作者和编辑流程
- 原创或获授权图片
- 可更新的长期 URL
- 清晰的内部链接
- 可验证的结构化数据
- 邮件和品牌受众
- 与创作者的真实合作关系

不要把“文章数量、社交账号数量或 Schema 数量”当作目标本身。真正的目标是让用户更快找到合适设计，并愿意继续浏览、订阅、分享和再次搜索品牌。
