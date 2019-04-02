# AMP相关介绍

> AMP 是一个开放源代码库，它提供了一种非常简单的方法，让您能够轻松地为用户创建富有吸引力、运行顺畅且几乎可即时完成加载的网页。AMP 网页其实只是可由您链接到和控制的网页而已。——— 引用官网的介绍

##### AMP缓存
###### AMP 缓存是一种基于代理的内容传送网络 (CDN)，用于传送有效的 AMP 文档。AMP 缓存旨在：
  1. 仅提供有效的 AMP 网页。
  2. 让 AMP 网页能够安全且高效地预加载。
  3. 对内容执行额外的性能优化措施，以提升用户体验。
##### 我的 AMP 网页是如何缓存的？
###### 使用 AMP 格式即意味着 AMP 缓存可以缓存您的内容。您的 AMP 网页可通过多种方式缓存在 AMP 缓存中：

- 平台发现：平台可通过 `<html ⚡> `或 `<html amp>` 标记发现您的 AMP 内容，进而缓存该内容。例如，Google 搜索会抓取内容；对于任何已被识别出的有效 AMP 网页，系统都会自动将相应内容添加到 Google AMP 缓存中。

- 缓存网址请求：平台可通过使用 AMP 缓存网址格式有针对性地请求访问某个 AMP 网页。在这种情况下，AMP 缓存便是充当了反向代理；因此，当相应平台访问该网页时，系统就会自动缓存该网页。
    - Cloudflare AMP 缓存网址示例：https://amp.cloudflare.com/c/foo.com/amp_document.html
    - Google AMP 缓存网址示例：https://foo-com.cdn.ampproject.org/c/s/foo.com/amp_document.html
> 注意 — AMP 缓存网址不是面向用户的网址，也就是说，用户通常不会通过这些网址来请求获取内容。

![img](https://www.ampproject.org/static/img/docs/platforms_accessing_cache.png)

##AMP相关结构

``` 
<!doctype html>
<html amp lang="en">
  <head>
    <meta charset="utf-8">
    <script async src="https://cdn.ampproject.org/v0.js"></script>
    <title>Hello, AMPs</title>
    <link rel="canonical" href="http://example.ampproject.org/article-metadata.html">
    <meta name="viewport" content="width=device-width,minimum-scale=1,initial-scale=1">
    <script type="application/ld+json">
      {
        "@context": "http://schema.org",
        "@type": "NewsArticle",
        "headline": "Open-source framework for publishing content",
        "datePublished": "2015-10-07T12:02:41Z",
        "image": [
          "logo.jpg"
        ]
      }
    </script>
    <style amp-boilerplate>body{-webkit-animation:-amp-start 8s steps(1,end) 0s 1 normal both;-moz-animation:-amp-start 8s steps(1,end) 0s 1 normal both;-ms-animation:-amp-start 8s steps(1,end) 0s 1 normal both;animation:-amp-start 8s steps(1,end) 0s 1 normal both}@-webkit-keyframes -amp-start{from{visibility:hidden}to{visibility:visible}}@-moz-keyframes -amp-start{from{visibility:hidden}to{visibility:visible}}@-ms-keyframes -amp-start{from{visibility:hidden}to{visibility:visible}}@-o-keyframes -amp-start{from{visibility:hidden}to{visibility:visible}}@keyframes -amp-start{from{visibility:hidden}to{visibility:visible}}</style><noscript><style amp-boilerplate>body{-webkit-animation:none;-moz-animation:none;-ms-animation:none;animation:none}</style></noscript>
  </head>
  <body>
    <h1>Welcome to the mobile web</h1>
  </body>
</html>
```
1. 代码结构`<!doctype html>`开头。中必须标记包含顶级 `<html ⚡> `标记（也可以使用` <html amp>`）

2. 包含`<head> `和 `<body>` 标记。

3. 包含 `<meta charset="utf-8">` 标记，以此作为其 `<head> `标记的第一个子级。

4. 包含 `<script async src="https://cdn.ampproject.org/v0.js"></script> `标记，
>包含并加载 AMP JS 库。

5. 在其 `<head> 内包含 <link rel="canonical" href="$SOME_URL">` 标记。

>指向常规 HTML 版 AMP HTML 文档，如果不存在此类 HTML 版本，则指向其自身。有关详情，请参阅使您的网页可被轻松发现。

6. 在其` <head> 标记内包含 <meta name="viewport" content="width=device-width`,`minimum-scale=1">` 标记。还建议您添加 `initial-scale=1`。

----

## 相关注意事项
1. 不能使用`link`引入样式，只能使用`<style amp-custom>`的内联样式表中的元素选择器来设置元素的样式。

2. 不能使用自己写的js只能使用官方定义的UI以及相关js

## 验证AMP

1. 相关开发者验证方式

> `#development=1`

例如：

> `http://localhost:8000/pets.html#development=1`
----
> 最后附上相关介绍网站 https://www.ampproject.org/zh_cn/
> 相关 UI使用库 https://ampbyexample.com/components/amp-carousel/