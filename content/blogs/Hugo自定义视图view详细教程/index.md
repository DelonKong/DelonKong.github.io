---
title: Hugo自定义视图view详细教程
summary: 本文提供Hugo中如何修改公开主题模板的视图view以达到网站布局自定义的目的。
date: 2025-07-09
type: docs
math: false
tags:
  - 
image:
  caption: ''
---



本文提供Hugo中如何修改公开主题模板的视图view以达到网站布局自定义的目的。

*keywords: Hugo view修改， Hugo view 视图修改，定制 Hugo view，Hugo 自定义，Hugo个性化* 

# 一、前言

## 2.1 View存储位置

`view`是某些block中的一种页面布局选择，如在hugo academic主题的`collection`这个block中有article-grid、card、date-title-summary、citation等选择。

View为HTML文件，默认存储在`layouts/paritals/views/`中，很多主题模板没有此文件夹，以hugo academic 主题为例，`layouts/parital`中只有`hooks`文件夹，可以自己建一个名为`views`的文件夹。自定义的view可以直接存在`views/`文件夹下，也可以新建`views/community/`。

```
├── layouts/partials					<-- 布局等模板文件
│   └── hooks							<-- 钩子文件，保存一些可复用性的代码
│   └── blox							<-- blok内容块文件，详见2.2  # block存储位置
│   └── views							<-- view文件，详见2.2
│   	└── community					<-- 自定义view文件
│   		└── custom-view.html		<-- 自定义view.html文件
│   		└── custom-view.start.html	<-- 自定义view.start.html文件(必须有)
│   		└── custom-view.end.html	<-- 自定义view.end.html文件
```

也可以将公开仓库中已有的view保存到此文件夹中直接进行使用

- 公开仓库：**[hugo-blox-builder](https://github.com/HugoBlox/hugo-blox-builder)**
- block文件在仓库中的存储位置：`hugo-blox-builder-main\modules\blox-tailwind\layouts\partials\views`

## 2.2 网页结构

<img src="./Hugo%E8%87%AA%E5%AE%9A%E4%B9%89%E8%A7%86%E5%9B%BEview%E8%AF%A6%E7%BB%86%E6%95%99%E7%A8%8B.assets/landing-page-wireframe.jpg" alt="Easily create customized landing pages" style="zoom: 67%;" />

在hugo中，图中的`section`中包含若干个`block`，比方说专门展示文字的`block`、专门用于项目的`block`、专门用于奖项展示的`block`。每个`block`又可以使用不同的`view`，如在展示文章的`block`中可以选择使用竖排`view`、横排`view`、图文`view`、仅文字`view`等。

`Header` 和`Footer`也可以视为`block`的一种。

`block`和`view`的配置主要在`content/_index.md`中。

# 二、注意事项

注意事项：

- `content/_index.md`中修改主页block信息，将view改成自定义view
- view只是将block对应的md文件中已有的信息重排，注意view对应的block中能够存储哪些信息。需要额外信息的话，可能需要修改对应的block HTML文件。
- `_index.md`中为YAML配置，**须严格执行缩进**
- 必须要有`.start.html`，如自定义view命名为

明白主要步骤之后就可以压榨GPT等一众机器人干活了，制造自己想要的网页布局。

# 三、示例

**需求：**

- 原始`citation.html`作为展示文章列表的一个view，可以显示文章作者、题目、期刊、时间等信息，并提供了点击题目之后跳转到详情页的功能。此功能很鸡肋，想要直接去掉。

`content/_index.md`中的部分内容：

```
sections:
- block: collection
    id: papers
    content:
      title: Recent Publications
      count: 5
      filters:
        folders:
          - publication
        featured_only: true
    design:
      view: community/citation #修改此处为自定义view
```

修改`desing/view`为自定义view明，`community/citation`代表存储在`community/`文件夹下的`citation.html`。

`layouts/paritals/views/citation-custom.html`中的部分内容：

```
  <!-- <a href="{{ $item.RelPermalink }}">{{ $item.Title }}</a>. -->
  <span class="underline">{{ $item.Title }}</span>
```

去掉了点击题目跳转的代码。