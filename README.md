# UI Dance 换图图库（自备图片）

把你收集的图按下面的文件夹放进去，每类 **1.jpg ~ 5.jpg**，插件就会用你的图替代随机图。

## 规格
- 每张 **800×800 JPG**，**< 150KB**（UI mock 够用，加载快）
- 命名严格用数字：`1.jpg` `2.jpg` … `5.jpg`
- 除 `portrait`（人物头像）外，**尽量不要人脸**
- 不必一次凑齐：只填你常用的品类，其余自动用 LoremFlickr 兜底

## 文件夹 ↔ 品类对照
| 文件夹 | 品类 | | 文件夹 | 品类 |
|---|---|---|---|---|
| `coffee` | 咖啡 | | `hotel-lobby` | 酒店大堂 |
| `milk-tea` | 茶饮 | | `king-room` | 大床房 |
| `cake` | 蛋糕甜品 | | `twin-room` | 双床房 |
| `chinese` | 中餐家常 | | `suite` | 套房/行政房 |
| `hotpot` | 川菜/火锅 | | `sea-view` | 海景房 |
| `bbq` | 烧烤/烤肉 | | `resort` | 民宿/度假村 |
| `japanese` | 日料 | | `pool-gym` | 酒店泳池 |
| `western` | 西餐 | | `street` | 城市街景 |
| `snacks` | 小吃/早餐 | | `food-close` | 美食特写 |
| `salad` | 健康轻食 | | `portrait` | 人物头像 |
| | | | `packaging` | 商品包装 |

## 怎么上线（国内可直连）
图不能打包进插件（Figma 内联 >2MB 会崩），要放在国内能访问、带 CORS 的 URL 上。
推荐 **jsdelivr + 公开 GitHub 仓库**：

1. 把这个 `assets/images/` 推到一个**公开** GitHub 仓库（或单独建一个图片仓库）。
2. 对应的图片直链就是：
   ```
   https://cdn.jsdelivr.net/gh/<你的账号>/<仓库>@<分支或tag>/assets/images/coffee/1.jpg
   ```
3. 把 BASE（到 `assets/images` 为止）告诉我，我填进 `src/ui/data/image-library.ts` 的 `CURATED_BASE`，
   并在 `CURATED_COUNTS` 里写上每个已填好的品类数量。

> 改图后想立即生效：jsdelivr 有缓存，建议每次更新打一个新的 git tag（如 `@v1`、`@v2`），
> 或用 commit hash 当版本号，链接换成新版本即可绕过缓存。

如果你有自己的图床/CDN（公开直链 + CORS + 国内可达），把 BASE 给我也一样能用。
