---
# Leave the homepage title empty to use the site title
title: Shashwat Pande
date: 2022-10-24
type: landing

sections:
  - block: about.biography
    id: about
    content:
      title: About
      # Choose a user profile to display (a folder name within `content/authors/`)
      username: admin
      
  - block: collection
    id: featured
    content:
      title: Publications
      filters:
        folders:
          - publication
        featured_only: true
    design:
      columns: '2'
      view: card
      
  - block: collection
    content:
      title: 
      #text: |-
      #  {{% callout note %}}
      #  Quickly discover relevant content by [filtering publications](./publication/).
      #  {{% /callout %}}
      filters:
        folders:
          - publication
        exclude_featured: false
    design:
      columns: '2'
      view: citation
      
  - block: collection
    id: posts
    content:
      title: Posts
      subtitle: ''
      text: ''
      # Choose how many pages you would like to display (0 = all pages)
      count: 5
      # Filter on criteria
      filters:
        folders:
          - post
        author: ""
        category: ""
        tag: ""
        exclude_featured: false
        exclude_future: false
        exclude_past: false
        publication_type: ""
      # Choose how many pages you would like to offset by
      offset: 0
      # Page order: descending (desc) or ascending (asc) date.
      order: desc
    design:
      # Choose a layout view
      view: compact
      columns: '2'
      
  - block: collection
    id: talks
    content:
      title: Seminars & Talks
      filters:
        folders:
          - event
    design:
      columns: '2'
      view: compact
      
  
  - block: contact
    id: contact
    content:
      title: Contact
      subtitle: If you would like to get in touch to discuss research, projects and(or) have a nice chat on data and decision making, feel free to email me at shashwatpande101@gmail.com. 
      text: |-
      # Contact (add or remove contact options as necessary)
      email: 
---
