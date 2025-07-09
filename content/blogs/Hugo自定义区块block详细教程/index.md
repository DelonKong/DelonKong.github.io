---
title: Hugo自定义区块block详细教程
summary: 本文提供Hugo中如何修改公开主题模板的Block以达到网站布局自定义的目的
date: 2025-07-09
type: docs
math: false
tags:
  - 
image:
  caption: ''
---



本文提供Hugo中如何修改公开主题模板的Block以达到网站布局自定义的目的。

*keywords: Hugo block 修改，定制 Hugo block，Hugo 自定义，Hugo个性化* 

# 一、前言

## 2.1 Block存储位置

Block为HTML文件，默认存储在`layouts/paritals/blox/`中，很多主题模板没有此文件夹，以hugo academic 主题为例，`layouts/parital`中只有`hooks`文件夹，可以自己建一个名为`blox`的文件夹。

```
├── layouts/partials		<-- 布局等模板文件
│   └── hooks				<-- 钩子文件，保存一些可复用性的代码
│   └── blox				<-- blok内容块文件，详见2.2  # block存储位置
│   └── views				<-- view文件，详见2.2
│   	└── community		<-- 自定义view文件
```

也可以将公开仓库中已有的Block保存到此文件夹中直接进行使用

- 公开仓库：**[hugo-blox-builder](https://github.com/HugoBlox/hugo-blox-builder)**
- block文件在仓库中的存储位置：`hugo-blox-builder-main\modules\blox-tailwind\layouts\partials\blox`

## 2.2 网页结构

<img src="./Hugo%E8%87%AA%E5%AE%9A%E4%B9%89%E6%A8%A1%E5%9D%97block%E8%AF%A6%E7%BB%86%E6%95%99%E7%A8%8B.assets/landing-page-wireframe.jpg" alt="Easily create customized landing pages" style="zoom: 67%;" />

在hugo中，图中的`section`中包含若干个`block`，比方说专门展示文字的`block`、专门用于项目的`block`、专门用于奖项展示的`block`。每个`block`又可以使用不同的`view`，如在展示文章的`block`中可以选择使用竖排`view`、横排`view`、图文`view`、仅文字`view`等。

`Header` 和`Footer`也可以视为`block`的一种。

`block`和`view`的配置主要在`content/_index.md`中。

# 二、修改主题模板自带block

参考网址：[🧱 Build your pages with blocks: no-code required! | Hugo Blox Docs](https://docs.hugoblox.com/getting-started/page-builder/)

注意事项：

- `content/_index.md`中修改主页block信息
- `config/_default/menus.yaml`中修改导航栏信息
- `_index.md`中为YAML配置，**须严格执行缩进**

# 三、自定义block

## 3.1 参考网址：

- [➕ Extend Hugo Blox | Hugo Blox Docs](https://docs.hugoblox.com/reference/extend/#recompile-tailwind)
- [HugoBlox/create-blox: 🧑‍🎨 Create and publish your very own content blocks for Hugo](https://github.com/HugoBlox/create-blox)

## 3.2 修改方式

自定义修改方式主要有两种：

- 直接在主题模板现有的Block上修改，仅修改布局显示等
- 自己建立新的Block文件进行修改

主要步骤：

- `layouts/paritals/blox/`中新建自定义block文件，如`block-custom.html`
- 用到css的话同样如此，也可直接写在HTML中
- 修改相应位置的md文件

明白主要步骤之后就可以压榨GPT等一众机器人干活了，制造自己想要的网页布局。

# 四、示例

**需求：**

- 原始`markdown.html`作为展示文字的一个Block，只能在`_index.md`配置文件中添加正文，对于想要分类展示不同信息来说，很不方便
- 建立一个可以直接读取markdown文件内容并可以分类独立展示的Block

原始`markdown.html`在`content/_index.md`中的配置展示：

文字只能写在text: |-后，不能用单独的文件存放。

```
- block: markdown
    content:
      title: '📚 My Research'
      subtitle: ''
      text: |-
        Use this area to speak to your mission. I'm a research scientist in the Moonshot team at DeepMind. I blog about machine learning, deep learning, and moonshots.
```

## 4.1 自定义.md文件配置

**目录结构：**

```
├── content/				<-- 内容文件
│   └── _index.md			<-- 主页内容配置
│   └── news/				
│   └── news.md			
│   └── competitions/				
│   └── competitions.md	
```

在`content/_index.md`中的配置如代码所示。

**目的：**

- 以文字形式**分别展示**news以及competitions
- 所对应的内容**分别存储**在`content/news/news.md`和`content/competitions/competitions.md`

```
sections:
 - block: markdown-custom # markdown  #   
    id: news
    content:
      title: 🔥 Recent News
      source: news/news
      show_title: true
      show_subtitle: false
  
  - block: markdown-custom
    id: competitions
    content:
      title: 🏆 Competitions
      source: competitions/competitions
      show_title: true
      show_subtitle: false
```

**content/news/news.md：**

注意：两个---中间的内容为YAML段落

```
---
title: "Recent News"
subtitle: ""
---

- *2025.06.29--07.06* : 👋 网站建立成功
- *2025.06.29--07.06* : 🏆 xxx比赛成功举办
```

## 4.2 markdown-custom.html

- `layouts/paritals/blox/`中新建自定义`markdown-custom.html`文件
- 修改HTML内容
- `block.content`获取`content/_index.md`中的相应配置，如，title、subtitle、source等
- source指内容存放目录，可以直接存放在`content/`下，也可以新建文件夹存放，如放置在`content/news/`
- `source: news/news`指的是：存放在`content/news/`下的`news.md`

```
{{/* Hugo Blox: Final Markdown block styled like citation.html */}}

{{ $page := .wcPage }}
{{ $block := .wcBlock }}

{{ $title := $block.content.title | emojify | $page.RenderString }}
{{ $subtitle := $block.content.subtitle | emojify | $page.RenderString }}
{{ $source := $block.content.source | default "news" }}
{{ $showTitle := $block.content.show_title | default true }}
{{ $showSubtitle := $block.content.show_subtitle | default false }}

{{ $target := site.GetPage "section" $source }}


{{ if not $target }}
  <div class="text-red-600">❌ Error: Section '{{ $source }}' not found.</div>
{{ else }}

  <section id="{{ $block.id }}" class="w-full px-4 sm:px-6 lg:px-8 mb-2">

    <div class="max-w-3xl mx-auto">

      {{ if $showTitle }}
        <div class="text-3xl font-bold text-gray-900 dark:text-white text-center mb-2">
          {{ with $title }}{{ . }}{{ else }}{{ $target.Title }}{{ end }}
        </div>
      {{ end }}

      {{ if and $showSubtitle (or $subtitle $target.Params.subtitle) }}
        <div class="text-2xl font-bold text-gray-900 dark:text-gray-300 text-center mb-4">
          {{ with $subtitle }}{{ . }}{{ else }}{{ $target.Params.subtitle }}{{ end }}
        </div>
      {{ end }}

      <div class="prose dark:prose-invert mt-8 text-base leading-snug w-full max-w-none text-left" >
        {{ $target.Content }}
      </div>

    </div>
  </section>

{{ end }}
```



