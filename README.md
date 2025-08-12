# MultiCDNSafeLoader

**MultiCDNSafeLoader** 是一个基于 JavaScript 的资源加载器，支持多 CDN 备份自动切换，配合 Subresource Integrity (SRI) 校验，确保资源安全、可靠且稳定加载。

## 功能特点

- 多个 CDN 地址按优先级顺序自动尝试加载资源  
- 资源完整性校验，防止篡改（支持 SHA-256/384/512）  
- 支持 CSS 和 JavaScript 资源  
- 自动检测加载失败，切换至备用 CDN  
- 支持本地资源和 CDN 资源统一管理  
- 保证 JavaScript 按顺序执行，避免依赖冲突  

## 使用方法

1. 编写资源配置 JSON，例如：

```json
{
  "cdn_prefixes": [
    "https://cdn.bytedance.com/cdn/expire-1-M/",
    "https://cdnjs.snrat.com/ajax/libs/",
    "https://cdn.staticfile.net/ajax/libs/",
    "https://cdn.bootcdn.net/ajax/libs/",
    "https://mirrors.sustech.edu.cn/cdnjs/ajax/libs/",
    "https://cdnjs.cloudflare.com/ajax/libs/"
  ],
  "resources": {
    "jquery": {
      "suffix": "jquery/3.6.0/jquery.min.js",
      "sri": "sha512-xxxxxx...",
      "use_cdn": true
    },
    "color_modes": {
      "suffix": "/static/js/color-modes.js",
      "sri": "sha512-yyyyyy...",
      "use_cdn": false
    }
  }
}
````

2. 在页面中引入 `MultiCDNSafeLoader` 脚本，加载并使用该配置

## 示例

请参考仓库中的 `example.html`，里面包含完整示例代码。

## 许可证

MIT License
