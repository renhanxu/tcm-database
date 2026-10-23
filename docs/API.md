# TCM Database API 文档

## 端点列表

### 1. 获取中药列表

**URL**: `/data/herbs.json`

**示例**:
```typescript
// App 中调用
const getHerbs = async () => {
  const url = 'https://cdn.jsdelivr.net/gh/renhanxu/tcm-database@main/data/herbs.json';
  const response = await fetch(url);
  const data = await response.json();
  return data.data;
};
```

### 2. 获取方剂列表

**URL**: `/data/formulas.json`

### 3. 获取版本信息

**URL**: `/data/index.json`

```json
{
  "version": "1.0.0",
  "updated_at": "2026-10-23T00:00:00Z",
  "herbs_count": 100,
  "formulas_count": 50
}
```

## 镜像站支持

国内用户推荐使用以下镜像加速:

- **jsDelivr**: `https://cdn.jsdelivr.net/gh/renhanxu/tcm-database@main/`
- **Ghproxy**: `https://ghproxy.com/https://raw.githubusercontent.com/renhanxu/tcm-database/main/`

## 缓存策略

```typescript
// App 中实现缓存
const CACHE_EXPIRY = 7 * 24 * 60 * 60 * 1000; // 7 天

const getCachedHerbs = async () => {
  const cache = await AsyncStorage.getItem('herbs_cache');
  const cacheTime = await AsyncStorage.getItem('herbs_cache_time');
  
  if (cache && cacheTime && Date.now() - Number(cacheTime) < CACHE_EXPIRY) {
    return JSON.parse(cache);
  }
  
  const data = await getHerbs();
  await AsyncStorage.setItem('herbs_cache', JSON.stringify(data));
  await AsyncStorage.setItem('herbs_cache_time', Date.now().toString());
  return data;
};
```

## 更新频率

- 数据每月更新一次
- 可以通过检查 `index.json` 中的 `updated_at` 字段判断是否有更新
