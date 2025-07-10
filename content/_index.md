---
# Leave the homepage title empty to use the site title
title: ""
date: 2025-06-29
type: landing

design:
  # Default section spacing
  spacing: "3rem"

sections:

  - block: resume-biography-3-custom # community/about # resume-biography-3
    content:
      # Choose a user profile to display (a folder name within `content/authors/`)
      username: admin
      text: ""
      # Show a call-to-action button under your biography? (optional)
      button:
        text: Download CV
        url: uploads/resume.pdf
    design:
      css_class: dark
      background:
        color: black
        image:
          # Add your image background to `assets/media/`.
          filename: Simple Shiny.svg
#Sprinkle.svg
#Simple Shiny.svg
          filters:
            brightness: 1.0
          size: cover
          position: center
          parallax: false

  - block: markdown
    content:
      title: '✨📚😍😎😆💕💖👌🤞✌🐱‍🏍👀✨'
      subtitle: ''
      text: |-
       <center>Welcome to Delon's personal website 👋</center>
          <center>Please reach out to collaborate 😃</center>
    design:
      columns: '1'
  

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
      view: community/publication-card #citation #  # 
      columns: '1'  # must be '1'


  - block: collection
    content:
      title: Other Publications
      text: ""
      count: 5
      filters:
        folders:
          - publication
        exclude_featured: true
    design: 
      view: citation
      columns: '1'

#  - block: collection
#    id: talks
#    content:
#      title: Recent & Upcoming Talks
#      filters:
#        folders:
#          - talks
#    design:
#      view: article-grid
#      columns: 1
  

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

  - block: markdown-custom
    id: awards
    content:
      title: 🏅 Honors and Awards
      source: awards/awards
      show_title: true
      show_subtitle: false

  # - block: collection
  #   id: project
  #   content:
  #     title: 🧱 Project
  #     count: 6
  #     filters:
  #       folders:
  #         - project
  #   design:
  #     view: article-grid
  #     columns: 3

  - block: collection
    id: blogs
    content:
      title: 🗃 Blogs & Notes
      count: 6
      filters:
        folders:
          - blogs
    design:
      view: article-grid
      columns: 3

  - block: markdown-custom
    id: service
    content:
      title: ⛵ Service
      source: service/service
      show_title: true
      show_subtitle: false


  # - block: collection
  #   id: diary
  #   content:
  #     title: Diary
  #     subtitle: ''
  #     text: ''
  #     # Page type to display. E.g. post, talk, publication...
  #     page_type: diary
  #     # Choose how many pages you would like to display (0 = all pages)
  #     count: 1
  #     # Filter on criteria
  #     filters:
  #       author: ""
  #       category: ""
  #       tag: ""
  #       exclude_featured: false
  #       exclude_future: false
  #       exclude_past: false
  #       publication_type: ""
  #       folders:
  #         - diary
  #     # Choose how many pages you would like to offset by
  #     offset: 0
  #     # Page order: descending (desc) or ascending (asc) date.
  #     order: desc
  #   design:
  #     # Choose a layout view
  #     view: date-title-summary
  #     # Reduce spacing
  #     spacing:
  #       padding: [0, 0, 0, 0]
---









