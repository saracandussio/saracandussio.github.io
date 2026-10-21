---
title: ""
date: 2022-10-24
type: landing

design:
  spacing: "6rem"

sections:
  - block: resume-biography-3
    content:
      username: sara-candussio
      text: ""
      button:
        text: Download CV
        url: resume.pdf
    design:
      css_class: dark
      background:
        color: black
        image:
          filename: stacked-peaks.svg
          filters:
            brightness: 1.0
          size: cover
          position: center
          parallax: false
  - block: markdown
    content:
      title: '🧠 My Research'
      subtitle: ''
      text: |-
        I'm interested in understanding the **generalization abilities of large language models (LLMs)**, identifying their limitations and exploring ways to encourage reasoning beyond memorization.

        My work sits at the intersection of **Neuro-Symbolic AI**, **Reinforcement Learning for NLP**, and **multi-agent systems**. I'm particularly fascinated by how symbolic structure can guide and constrain neural learning.

        Feel free to reach out if you'd like to collaborate! 😃
    design:
      columns: '1'
  - block: collection
    id: talks
    content:
      title: Talks
      page_type: event
    design:
      view: article-grid
      columns: 2
  - block: collection
    id: news
    content:
      title: News
      count: 0
      filters:
        folders:
          - news
    design:
      view: timeline
      columns: 1
  - block: collection
    id: teaching
    content:
          title: Teaching
          page_type: teaching
          filters:
            folders:
              - teaching
  - block: collection
    id: papers
    content:
      title: Featured Publications
      page_type: publication
      filters:
        folders:
          - publication
        featured_only: true
    design:
      view: article-grid
      columns: 2
      fill_image: false
  - block: collection
    content:
      title: Recent Publications
      text: ""
      filters:
        folders:
          - publication
        exclude_featured: true
    design:
      view: citation
---
