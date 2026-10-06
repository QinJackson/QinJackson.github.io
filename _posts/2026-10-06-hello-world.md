---
title: 博客上线了
date: 2026-10-06 22:45:00 +0800
categories: [随笔]
tags: [Jekyll, Chirpy, GitHub Pages]
---

## 你好，世界

这是本站的第一篇文章，用来验证从提交代码到站点上线的整条流水线是否通畅。

### 这套博客是怎么搭起来的

| 环节 | 用到的工具 |
|---|---|
| 站点生成 | Jekyll + Chirpy 主题 |
| 托管 | GitHub Pages |
| 构建与部署 | GitHub Actions（仓库自带 `pages-deploy.yml`） |
| 评论 | 待接入 giscus（基于 GitHub Discussions） |
| 搜索 | 主题自带静态搜索 |

### 怎么写下一篇

在 `_posts/` 目录下新建 `YYYY-MM-DD-文件名.md`，写好开头的 front matter 就能发布：

```yaml
---
title: 文章标题
date: 2026-10-06 22:45:00 +0800
categories: [分类]
tags: [标签一, 标签二]
---
```

正文用 Markdown 写即可。推送到 `main` 分支后，Actions 会自动构建并发布到站点。

> 文件名必须以 `YYYY-MM-DD-` 开头，文件名尽量用英文（它会变成文章 URL 的一部分）；如果日期是未来时间，默认不会被生成。
{: .prompt-info }
