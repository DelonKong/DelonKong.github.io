---
title: "MHIAIFormer: Multihead Interacted and Adaptive Integrated Transformer With Spatial-Spectral Attention for Hyperspectral Image Classification"
authors:
- admin
- Jiahua Zhang
- Shichao Zhang
- Xiang Yu
- Foyez Ahmed Prodhan

author_notes:
# - "Equal contribution"
# - "Equal contribution"

ESI: "false"  # false true
tags:
# - Source Themes
featured: true


date: "2024-08-09T00:00:00Z"
doi: "10.1109/JSTARS.2024.3441111"

# Schedule page publish date (NOT publication's date).
publishDate: ""

# Publication type.
publication_types: ["article-journal"]

# Publication name and optional abbreviated publication name.
publication: "*IEEE Journal of Selected Topics in Applied Earth Observations and Remote Sensing*"
publication_short: "JSTARS"

abstract: Deep learning is an effective method for hyperspectral image (HSI) classification, where CNN-based and Transformerbased methods have achieved excellent performance. However, there are some drawbacks to the existing CNN-based and Transformer-based HSI classification approaches. 1) CNN-based methods are deficient in showing the extraction of multiscale features and localized features owing to the fixed-size input patch. 2) the MHSA module ignores the interaction capability between multiple attention heads, which leads to insufficient feature fusion in various directions. 3) The weights of attention heads in various directions are disregarded in the MHSA and attention heads are simply concatenated horizontally. To address the abovementioned limitations, a novel multihead interacted and adaptive integrated transformer (MHIAIFormer) with spatial-spectral attention, which integrates the respective advantages of convolutions and transformers is proposed in this study. A pyramidal spatialspectral attention (PS2A) feature extraction module is adopted to efficiently capture the localized and multiscale feature information of HSI. The output of PS2A is then sent to the transformer encoder stage through a grouped multiscale cross-dimension embedding module, which includes additive self-attention using multihead interaction and MHSA with adaptive multihead merging to capture the long-range dependencies of the features. Extensive experiments on four datasets verify that our proposed approach achieves more satisfactory classification accuracy when compared with stateof-the-art models. The overall accuracy of the proposed model achieved 95.97%, 98.68%, 92.68%, and 99.49% on four datasets.

# Summary. An optional shortened abstract.
summary: A novel multihead interacted and adaptive integrated transformer (MHIAIFormer) with spatial-spectral attention, which integrates the respective advantages of convolutions and transformers is proposed.

# links:
# - name: ""
#   url: ""
url_pdf: https://ieeexplore.ieee.org/document/10632582
url_code: 'https://github.com/DelonKong/MHIAIFormer'
url_dataset: ''
url_poster: ''
url_project: ''
url_slides: ''
url_source: ''
url_video: ''

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder. 
image:
  caption: 'MHIAIFormer'
  focal_point: ""
  preview_only: false #true 就是不显示


reading_time: false  # Show estimated reading time?
share: false  # Show social sharing links?
profile: false  # Show author profile?
comments: false  # Show comments?



# Associated Projects (optional).
#   Associate this publication with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `internal-project` references `content/project/internal-project/index.md`.
#   Otherwise, set `projects: []`.
projects: []
projects:
  - example

# Slides (optional).
#   Associate this publication with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides: "example"` references `content/slides/example/index.md`.
#   Otherwise, set `slides: ""`.
slides: 
---
