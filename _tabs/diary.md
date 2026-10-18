---
layout: page
icon: fas fa-book-open
order: 1
title: 日记
---

{% include lang.html %}
{% assign docs = site.diary | sort: 'date' | reverse %}

<div id="diary-list" class="pl-xl-2">
  <p class="text-muted">
    这里是我的日记与随记：记录学习、生活与当天想明白的事。
  </p>

  {% if docs.size == 0 %}
    <div class="p-4 text-center text-muted border rounded">
      还没有日记。第一篇写好后会出现在这里。
    </div>
  {% else %}
    <ul class="list-unstyled">
      {% for d in docs %}
        <li class="d-flex justify-content-between align-items-baseline py-2 border-bottom">
          <div class="me-3">
            <a href="{{ d.url | relative_url }}" class="h6 no-text-decoration">{{ d.title }}</a>
            {% if d.description %}
              <div class="small text-muted mt-1">{{ d.description }}</div>
            {% endif %}
            {% if d.tags.size > 0 %}
              <div class="small text-muted mt-1">
                {% for tag in d.tags %}
                  <span class="me-2">#{{ tag }}</span>
                {% endfor %}
              </div>
            {% endif %}
          </div>
          <div class="text-muted small text-nowrap">
            {% include datetime.html date=d.date lang=lang %}
          </div>
        </li>
      {% endfor %}
    </ul>
  {% endif %}
</div>

---

## 写作规范（手机端照着填就行）

### 1. 文件名

```
YYYY-MM-DD-slug.md
```

例：`2026-10-07-first-diary.md`

- 日期用**真实日期**，slug 用英文小写短横线（不要中文，避免 URL 编码问题）
- 一天可以写多篇：slug 不同即可

### 2. 开头（front matter）模板

```yaml
---
title: 标题
date: 2026-10-07 21:30:00 +0800
tags: [日记, 学习]
description: 一句话摘要（可选，显示在列表里）
---
```

- `tags` 里 **`日记` 固定写上**，再加主题标签（见第 3 条）
- `description` 可以不写，但写了列表页会更好看

### 3. 标签怎么选

| 标签 | 什么时候用 |
|---|---|
| `日记` | **每篇都加**（固定） |
| `学习` | 上课、看书、写代码、做题 |
| `生活` | 日常、宿舍、吃饭、心情 |
| 科目名 | 需要时再加，例如 `高等数学`、`C语言`、`OpenWrt` |

例：`tags: [日记, 学习, 高等数学]`

### 4. 正文

- 直接用 Markdown 写，`##` 是二级标题（会进右侧目录）
- 代码用三个反引号包起来，并标注语言（`bash` / `c` / `python`）
- 图片：先上传到 `assets/img/diary/`，然后写

```
![说明](/assets/img/diary/2026-10-07-photo.jpg)
```

### 5. 手机端怎么发

**方式一（Pages CMS 后台，推荐）**

1. 手机浏览器打开 **https://app.pagescms.org**
2. 用 **GitHub 账号登录**；第一次会让你授权一个 GitHub App（只给这一个仓库的读写权限）
3. 选中仓库 `QinJackson/QinJackson.github.io`
4. 左侧点 **日记** → 右上角 **新建**
5. 填标题、日期时间、标签（第一个必须选「日记」）、摘要（可选）、正文
6. 点保存 → 它会自动 commit 到仓库 → 约 1 分钟站点自动更新

字段表单已配好，不用手写 front matter；文件名也会按 `年-月-日-标题.md` 自动生成。

**方式二（GitHub 网页，后台临时不可用时）**

手机打开仓库 → `_diary/` → Add file → Create new file → 文件名 `2026-10-07-slug.md` → 粘贴第 2 节的 front matter 模板 → 写正文 → Commit changes。

### 6. 图片体积提醒

手机直出照片常是 3–5 MB。上传前建议压到 **300 KB 以内**（微信发给自己再保存、或系统相册的"压缩"选项都行）。整站现在是几百 KB 级别，保持住才能加载快。
