# Frontend Performance Checklist

[中文](./README-zh-CN.md)

## INTRO

This project offers essential frontend performance optimization checkpoints to rapidly improve performance metrics.

## CORE PRINCIPLES

- **Smaller Size**: Minimize resource size through compression, code cleanup, and efficient formats.
- **Faster Rendering**: Speed up page display by optimizing the critical rendering path and reducing blocking.
- **Greater Reuse**: Leverage caching, CDN, and reusable components to avoid redundant requests and rendering.

## CHECKLIST

### Monitoring

- Conduct performance audits with Chrome DevTools - [Lighthouse](https://developer.chrome.com/docs/lighthouse) and [Performance](https://developer.chrome.com/docs/performance) Tabs
- Monitor [Web Vitals](https://github.com/GoogleChrome/web-vitals) (LCP, FID, CLS)

### Build Assets Optimization

All modern development supports optimization during the build process, including code compression, removal of unused code blocks and comments. Here are some key points to focus on:

- Scan and analyze final bundled files using tools like [Webpack Bundle Analyzer](https://github.com/webpack-contrib/webpack-bundle-analyzer) or [vite-bundle-analyzer](https://github.com/nonzzz/vite-bundle-analyzer)
- Disable developer mode and remove sourcemaps during build to reduce size
- Verify [Tree shaking](https://developer.mozilla.org/en-US/docs/Glossary/Tree_shaking) and [Code splitting](https://developer.mozilla.org/en-US/docs/Glossary/Code_splitting) are working as expected
- Optimize Code splitting arrangement for best resource loading process
- Reduce unnecessary dependencies and third-party library usage

### Resource Loading Optimization

- Use CDN
- Implement proper caching and minimize cache impact from code updates
- Use preload for priority resource handling
- Use prefetch to load and cache resources during idle time
- Use preconnect and dns-prefetch to speed up connection establishment
- Load certain resources asynchronously

### Media (Image) Loading Optimization

- Choose appropriate image formats
  <details>
    <summary>Details</summary>
    <ul>
      <li>Prioritize WebP format</li>
      <li>Use fonts or SVG for icons</li>
      <li>Use progressive images to enhance user experience</li>
    </ul>
  </details>
- Compress images and select appropriate sizes
- Balance quality and file size
- Implement lazy loading
- Use image proxy services or image storage services to select better formats and sizes, such as [IPX](https://www.npmjs.com/package/ipx) or [Cloudflare Images](https://developers.cloudflare.com/images/)
- Use responsive images

### Rendering Performance

- Prioritize CSS animations
- Use `font-display: swap` to optimize text loading and rendering
- Implement virtual lists for large data display
- Reduce Reflow and Repaint

### JS Performance

- Avoid memory leaks (clean up timers, event listeners)
- Optimize event listeners with Debounce and Throttle
- Use Web Workers for long-running tasks that block the main process

### Network Request Optimization

- Use HTTP/2 or HTTP/3
- Enable Gzip or Brotli compression
- Reduce HTTP request count (combine resources)

#### Additional Resources

- https://developer.mozilla.org/en-US/docs/Web/Performance
- https://web.dev/learn/performance
- https://developer.chrome.com/docs/performance
- https://developer.chrome.com/docs/lighthouse/performance/performance-scoring
