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
  - block: research-featured
    id: papers
    content:
      featured_title: Selected Publications
      interests:
        - Faithful LLM Reasoning
        - Chain-of-Thought
        - Interpretability
        - AI Safety
      title: '🧠 My Research'
      subtitle: ''
      text: |-
        I study **how large language models reason**, and whether what they write actually reflects what they compute. Much of my recent work focuses on **Chain-of-Thought in large reasoning models**: when it is faithful, when it is epiphenomenal, and how much of it can be compressed away.

        I'm also interested in **interpretability and control** (e.g. steering models with sparse autoencoders under hard constraints) and in **AI safety**, from detecting deception in dialogue to making LLMs more robust through multi-agent debate.

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
    id: teaching
    content:
          title: Teaching
          page_type: teaching
          filters:
            folders:
              - teaching
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
