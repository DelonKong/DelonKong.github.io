---
title: "Co-authors"
type: landing
sections:
  - block: collection
    id: coauthors
    content:
      title: "🎁 Characters"
      filters:
        folders:
          - authors 
    design:
      view: community/coauthors-card
      columns: 1
      # 头像处理
      avatar_fit: "200x200"       # 控制图片处理尺寸（原图处理）
      avatar_width: "200px"       # 控制最终显示尺寸
      avatar_shape: rounded-lg  # 控制圆角
      # 页面宽度控制
      center: true  # 控制是否居中（true=固定宽度居中，false=全屏）
    logic:
      filter_packet: false 

  #  - block: testimonials
  #    content:
  #      items:
  #        - text: "这是一项伟大的创新，我非常推荐！"
  #          image: authors/LittleM/avatar.jpg

  # - block: collection
  #   id: coauthors
  #   content:
  #     title: "👥 Co-authors"
  #     filters:
  #       folders:
  #         - authors 
  #   design:
  #     view: community/coauthors-card
  #     columns: 2
  #     # 头像处理
  #     avatar_fit: "200x200"       # 控制图片处理尺寸（原图处理）
  #     avatar_width: "200px"       # 控制最终显示尺寸
  #     avatar_shape: rounded-lg  # 控制圆角
  #     # 页面宽度控制
  #     center: false # 控制是否居中（true=固定宽度居中，false=全屏）
  #   logic:
  #     filter_packet: true


---

