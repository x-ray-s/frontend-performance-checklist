# 前端性能优化清单

[English](./README.md)

## 简介

本项目提供前端性能优化的关键检查点，帮助快速提升性能指标。

## 核心原则

- **更小的体积**：通过压缩、代码清理和高效格式来最小化资源大小
- **更快的渲染**：通过优化关键渲染路径和减少阻塞来加速页面显示
- **更好的复用**：利用缓存、CDN 和可复用组件来避免重复请求和渲染

## 检查清单

### 监控

- 使用 Chrome DevTools 进行性能审计 - [Lighthouse](https://developer.chrome.com/docs/lighthouse) 和 [Performance](https://developer.chrome.com/docs/performance) 标签页
- 监控 [Web Vitals](https://github.com/GoogleChrome/web-vitals) (LCP, FID, CLS)

### 构建资源优化

所有现代化开发都支持构建过程中进行优化，包括压缩代码体积，删除未使用的代码块和注释，这里列举几个需要关注的点

- 扫描并分析最终打包后文件，例如[Webpack Bundle Analyzer](https://github.com/webpack-contrib/webpack-bundle-analyzer) 或 [vite-bundle-analyzer](https://github.com/nonzzz/vite-bundle-analyzer)
- 构建时关闭开发者模式并移除 sourcemap 以减少体积
- 检查 [Tree shaking](https://developer.mozilla.org/zh-CN/docs/Glossary/Tree_shaking) 和 [Code splitting](https://developer.mozilla.org/zh-CN/docs/Glossary/Code_splitting) 是否符合预期
- 合理的编排 Code splitting 以获取最佳的加载资源过程
- 减少不必须要的依赖和三方库的使用

### 资源加载优化

- 使用 CDN
- 合理使用缓存并减少更新代码对缓存的影响
- 使用 preload 来优先处理资源
- 使用 prefetch 利用空闲时间加载和缓存资源
- 使用 preconnect 和 dns-prefetc 加速连接的建立
- 异步加载某些资源

### 媒体（图片）加载优化

- 合理使用图片格式
  <details>
        <summary>详情<summary>
        <ul>
            <li>优先使用 WebP 格式</li>
            <li>使用 font 或 svg 制作 Icon</li>
            <li>使用渐进式图片来提升用户体验</li>
        </ul>
    </details>
- 压缩图片和选择合适的尺寸
- 在质量与大小之间保持平衡
- 使用懒加载
- 使用图片代理服务或图片存储服务来选择更合适的图片格式和尺寸，例如 [IPX](https://www.npmjs.com/package/ipx) 或 [Cloudflare Images](https://developers.cloudflare.com/images/)
- 使用响应式图片

### 渲染性能

- 优先使用 CSS 动画
- `font-display: swap` 优化文字加载渲染
- 使用虚拟列表处理大数据展示
- 减少重排（Reflow）和重绘（Repaint）

### JS 性能

- 避免内存泄漏（清理定时器、事件监听）
- 防抖（Debounce）和节流（Throttle）优化事件监听
- 使用 Web Worker 处理阻塞进程的长任务

### 网络请求优化

- 使用 HTTP/2 或 HTTP/3
- 开启 Gzip 或 Brotli 压缩
- 减少 HTTP 请求数量（合并资源）

#### 更多资源

- https://developer.mozilla.org/zh-CN/docs/Web/Performance
- https://web.dev/learn/performance
- https://developer.chrome.com/docs/performance
- https://developer.chrome.com/docs/lighthouse/performance/performance-scoring?hl=zh-cn
