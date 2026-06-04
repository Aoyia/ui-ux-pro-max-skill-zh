# 资产组织指南

旨在通过结构化、可搜索的系统来组织市场营销资产的指南。

## 目录结构

```
project-root/
├── .assets/                          # Git 追踪的元数据
│   ├── manifest.json                 # 中央资产注册表
│   ├── tags.json                     # 标签系统
│   ├── versions/                     # 版本历史
│   │   └── {asset-id}/
│   │       └── v{n}.json
│   └── metadata/                     # 特定类型的元数据
│       ├── designs.json
│       ├── banners.json
│       ├── logos.json
│       └── videos.json
├── assets/                           # 原始文件
│   ├── designs/
│   │   ├── campaigns/                # 特定营销活动的活动设计
│   │   ├── web/                      # 网站图形
│   │   └── print/                    # 印刷材料
│   ├── banners/
│   │   ├── social-media/             # 平台横幅
│   │   ├── email-headers/            # 邮件模板页眉
│   │   └── landing-pages/            # 首屏/各版块图像
│   ├── logos/
│   │   ├── full-horizontal/          # 带有文字标识的完整横向标志
│   │   ├── icon-only/                # 仅图标/符号
│   │   ├── monochrome/               # 单色版本
│   │   └── variations/               # 特殊变体/版本
│   ├── videos/
│   │   ├── ads/                      # 促销/广告视频
│   │   ├── tutorials/                # 教程/指南内容
│   │   └── testimonials/             # 客户见证视频
│   ├── infographics/                 # 信息图/数据可视化
│   └── generated/                    # AI 生成的资产
│       └── {YYYYMMDD}/               # 按日期组织
```

## 命名规范

### 格式
```
{type}_{campaign}_{description}_{timestamp}_{variant}.{ext}
```

### 组成部分
| 组成部分 | 格式 | 是否必填 | 示例 |
|-----------|--------|----------|----------|
| type | 小写字母 | 是 | banner, logo, design, video |
| campaign | kebab-case | 是* | claude-launch, q1-promo, evergreen |
| description | kebab-case | 是 | hero-image, email-header |
| timestamp | YYYYMMDD | 是 | 20251209 |
| variant | kebab-case | 否 | dark-mode, 1x1, mobile |

*非营销活动资产使用 "evergreen"

### 示例
```
banner_claude-launch_hero-image_20251209_16-9.png
logo_brand-refresh_horizontal-full-color_20251209.svg
design_holiday-campaign_email-hero_20251209_dark-mode.psd
video_product-demo_feature-walkthrough_20251209.mp4
infographic_evergreen_pricing-comparison_20251209.png
```

## 元数据模式 (Metadata Schema)

### 资产条目 (manifest.json)
```json
{
  "id": "uuid-v4",
  "name": "Campaign Hero Banner",
  "type": "banner",
  "path": "assets/banners/landing-pages/banner_claude-launch_hero-image_20251209.png",
  "dimensions": { "width": 1920, "height": 1080 },
  "fileSize": 245760,
  "mimeType": "image/png",
  "tags": ["campaign", "hero", "launch"],
  "status": "approved",
  "source": {
    "model": "imagen-4",
    "prompt": "...",
    "createdAt": "2025-12-09T10:30:00Z"
  },
  "version": 2,
  "createdBy": "agent:content-creator",
  "approvedBy": "user:john",
  "approvedAt": "2025-12-09T14:00:00Z"
}
```

### 版本条目 (versions/{id}/v{n}.json)
```json
{
  "version": 2,
  "previousVersion": 1,
  "path": "assets/banners/landing-pages/banner_claude-launch_hero-image_20251209_v2.png",
  "changes": "Updated CTA button color to match brand refresh",
  "createdAt": "2025-12-09T12:00:00Z",
  "createdBy": "agent:ui-designer"
}
```

## 标签系统

### 标准标签
| 类别 | 值 |
|----------|--------|
| status | draft, review, approved, archived |
| platform | instagram, twitter, linkedin, facebook, youtube, email, web |
| content-type | promotional, educational, brand, product, testimonial |
| format | 1x1, 4x5, 9x16, 16x9, story, reel, banner |
| source | imagen-4, veo-3, user-upload, canva, figma |

### 标签使用规范
- 每个资产都应包含：状态 (status) + 平台 (platform) + 内容类型 (content-type)
- 可选：格式 (format)、来源 (source)、营销活动 (campaign)

## 文件组织最佳实践

1. **每个变体对应一个文件** - 不要把深色/浅色合并在一个文件中。
2. **源文件独立存放** - 将 .psd/.fig 文件保存在相同的目录结构中。
3. **AI 资产标记时间戳** - 按生成日期自动组织。
4. **归档而非删除** - 移动到 `archived/` 目录并加上日期前缀。
5. **大文件外部存储** - 超过 100MB 的视频使用云存储链接。

## 搜索模式

### 按类型
```bash
# 查找所有横幅 (banner)
ls assets/banners/**/*
```

### 按营销活动
```bash
# 查找特定营销活动的所有资产
grep -l "claude-launch" .assets/manifest.json
```

### 按状态
```bash
# 仅查找已批准的资产
jq '.assets[] | select(.status == "approved")' .assets/manifest.json
```

## 清理工作流

1. 对新资产运行 `extract-colors.cjs`。
2. 根据品牌指南进行验证。
3. 使用新条目更新 manifest.json。
4. 添加适当的标签。
5. 移除重复/过期的版本。
