# 性能优化检查清单

常见的页面加载性能优化项，按类别分组，供分析时参考。

## 资源加载优化

| 优化项 | 具体措施 | 影响指标 |
|--------|----------|----------|
| 图片优化 | 使用 WebP/AVIF 格式、适当压缩、设置合理尺寸 | LCP, SI |
| 图片懒加载 | 对首屏以下图片使用 `loading="lazy"` | LCP, SI |
| 关键资源预加载 | 使用 `<link rel="preload">` 预加载关键字体、图片 | LCP, FCP |
| 字体优化 | 使用 `font-display: swap`、子集化字体、预加载字体文件 | FCP, CLS |
| 减少请求数量 | 合并小文件、使用雪碧图或 SVG 内联 | FCP, SI |
| 资源压缩 | 启用 Gzip/Brotli 压缩 | FCP, LCP, TTFB |
| CDN 加速 | 将静态资源部署到 CDN | TTFB, FCP, LCP |
| HTTP 缓存 | 设置合理的 Cache-Control 和 ETag | TTFB, FCP |

## JavaScript 优化

| 优化项 | 具体措施 | 影响指标 |
|--------|----------|----------|
| 代码分割 | 使用动态 `import()` 按路由/组件分割代码 | FCP, LCP, INP |
| Tree Shaking | 确保构建工具移除未使用的代码 | FCP, LCP |
| 延迟加载非关键 JS | 使用 `defer` 或 `async` 属性 | FCP, INP |
| 减少主线程阻塞 | 拆分长任务、使用 Web Worker | INP |
| 第三方脚本优化 | 延迟加载第三方脚本、使用 `loading="lazy"` 加载 iframe | FCP, LCP, INP |
| 减少 Bundle 体积 | 分析并移除未使用的依赖、使用轻量替代库 | FCP, LCP |

## CSS 优化

| 优化项 | 具体措施 | 影响指标 |
|--------|----------|----------|
| 关键 CSS 内联 | 将首屏关键 CSS 内联到 HTML `<head>` 中 | FCP |
| 移除未使用 CSS | 使用 PurgeCSS 等工具移除无用样式 | FCP |
| 避免 CSS @import | 使用 `<link>` 替代 `@import` 减少请求链 | FCP |
| 减少 CSS 选择器复杂度 | 简化嵌套选择器，减少样式计算时间 | INP |

## 布局稳定性优化

| 优化项 | 具体措施 | 影响指标 |
|--------|----------|----------|
| 图片/视频设置尺寸 | 为 `<img>` 和 `<video>` 设置 `width` 和 `height` 属性 | CLS |
| 预留广告/嵌入位空间 | 为动态内容预留固定尺寸的容器 | CLS |
| 避免动态注入内容 | 避免在已有内容上方插入新元素 | CLS |
| Web 字体闪烁 | 使用 `font-display: optional` 或预加载字体 | CLS |
| 使用 CSS `contain` | 对独立组件使用 `contain: layout` 限制重排范围 | CLS, INP |

## 服务端优化

| 优化项 | 具体措施 | 影响指标 |
|--------|----------|----------|
| 减少服务端响应时间 | 优化数据库查询、使用缓存、升级服务器配置 | TTFB |
| 使用 SSR/SSG | 服务端渲染或静态生成减少客户端渲染时间 | FCP, LCP |
| 启用 HTTP/2 或 HTTP/3 | 利用多路复用减少连接开销 | FCP, LCP |
| 预连接关键域名 | 使用 `<link rel="preconnect">` 提前建立连接 | TTFB, FCP |
| DNS 预解析 | 使用 `<link rel="dns-prefetch">` 提前解析域名 | TTFB |

## 渲染优化

| 优化项 | 具体措施 | 影响指标 |
|--------|----------|----------|
| 减少 DOM 节点数量 | 简化 DOM 结构，避免过深嵌套 | INP, FCP |
| 使用虚拟列表 | 对长列表使用虚拟滚动 | INP |
| 避免强制同步布局 | 避免在 JS 中交替读写 DOM 属性 | INP |
| 使用 `requestAnimationFrame` | 将视觉更新放入 rAF 回调 | INP |
| 使用 CSS `will-change` | 对即将动画的元素提示浏览器提前优化 | INP |

## 指标评级参考

### Core Web Vitals 阈值（Google 官方标准）

| 指标 | 好 (🟢) | 需改进 (🟡) | 差 (🔴) |
|------|---------|-------------|---------|
| LCP | ≤ 2.5s | 2.5s - 4.0s | > 4.0s |
| FCP | ≤ 1.8s | 1.8s - 3.0s | > 3.0s |
| CLS | ≤ 0.1 | 0.1 - 0.25 | > 0.25 |
| INP | ≤ 200ms | 200ms - 500ms | > 500ms |
| TTFB | ≤ 800ms | 800ms - 1800ms | > 1800ms |
| SI | ≤ 3.4s | 3.4s - 5.8s | > 5.8s |
