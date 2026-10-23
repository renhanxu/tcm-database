# TCM Database (中医药材数据库)

Traditional Chinese Medicine Herbs and Formulas Database with images and metadata.

## 数据来源

- **中医文献**: 借用自 [lab99x/tcmoc](https://github.com/lab99x/tcmoc) 项目
- **中药图片**: 搜狗百科、维基百科、公开资源

## 项目结构

```
├── data/
│   ├── herbs.json          # 中药材元数据
│   ├── formulas.json       # 常用方剂
│   └── index.json          # 数据版本信息
├── images/
│   ├── herbs/              # 中药材图片 (WebP)
│   └── formulas/           # 方剂图片
├── scripts/
│   ├── scrape_herbs.py     # 爬取中药数据
│   └── upload.py           # 上传脚本
└── docs/
    └── API.md              # API 调用文档
```

## API 使用

### 获取所有中药

```bash
curl https://raw.githubusercontent.com/renhanxu/tcm-database/main/data/herbs.json
```

### 使用镜像站 (国内推荐)

```bash
# jsDelivr CDN
https://cdn.jsdelivr.net/gh/renhanxu/tcm-database@main/data/herbs.json

# Ghproxy (Gitee 镜像)
https://ghproxy.com/https://raw.githubusercontent.com/renhanxu/tcm-database/main/data/herbs.json
```

## 数据格式

### herbs.json
```json
{
  "version": "1.0.0",
  "updated_at": "2026-10-23T00:00:00Z",
  "count": 100,
  "data": [
    {
      "id": "1",
      "name": "黄芪",
      "pinyin": "huang_qi",
      "english": "Astragalus",
      "image": "herbs/huangqi.webp",
      "effects": ["补气固表", "利水消肿"],
      "taste": "甘",
      "meridians": ["脾经", "肺经"],
      "dosage": "10-30g",
      "usage": "煎服"
    }
  ]
}
```

## 许可证

MIT License - 使用本数据时请注明来源

## 致谢

感谢 [lab99x](https://github.com/lab99x) 的 tcmoc 项目提供的中医文献资源。
