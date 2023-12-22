---
# Leave the homepage title empty to use the site title
title: 
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
      
  - block: portfolio
    id: projects
    content:
      title: Projects
      filters:
        folders:
          - project
      # Default filter index (e.g. 0 corresponds to the first `filter_button` instance below).
      default_button_index: 0
      # Filter toolbar (optional).
      # Add or remove as many filters (`filter_button` instances) as you like.
      # To show all items, set `tag` to "*".
      # To filter by a specific tag, set `tag` to an existing tag name.
      # To remove the toolbar, delete the entire `filter_button` block.
      buttons:
        - name: All
          tag: '*'
        - name: Data Science
          tag: Data Science
        - name: Decision Making
          tag: Decision Making
    design:
      # Choose how many columns the section has. Valid values: '1' or '2'.
      columns: '1'
      view: showcase
      # For Showcase view, flip alternate rows?
      flip_alt_rows: false
      
  - block: experience
    content:
      title: Experience
      # Date format for experience
      #   Refer to https://wowchemy.com/docs/customization/#date-format
      date_format: Jan 2006
      # Experiences.
      #   Add/remove as many `experience` items below as you like.
      #   Required fields are `title`, `company`, and `date_start`.
      #   Leave `date_end` empty if it's your current employer.
      #   Begin multi-line descriptions with YAML's `|2-` multi-line prefix.
      items:
        - title: Lead Data Scientist
          company: Triumph Motorcycles Ltd.
          company_url: 'https://www.triumphmotorcycles.co.uk/'
          location: Hinckley, Leicestershire
          date_start: '2022-05-01'
          date_end: ''
          description: Partnering with clients across the business to define problems, identify data, develop models, build systems and bring a data-driven approach to decision-making.
        - title: Visiting Researcher
          company: Loughborough University
          company_url: 'https://www.lboro.ac.uk/departments/sbe/cim/'
          location: Loughborough, Leicestershire
          date_start: '2022-05-01'
          date_end: ''
          description: Conducting basic and applied research in data science and decision-making.
        - title: KTP Associate (Data Scientist)
          company: Loughborough University
          company_url: 'https://www.lboro.ac.uk/'
          location: Loughborough, Leicestershire
          date_start: '2020-03-01'
          date_end: '2022-04-30'
          description: Managed the delivery of a transformational innovation project for the commercialisation of research carried out at the Center for Information Management jointly funded (£200,000) by Triumph Motorcyles Ltd. and the UKRI (through Innovate UK).
        - title: Class Teacher
          company: London School of Economics and Political Science
          company_url: 'https://www.lse.ac.uk/'
          location: Holborn, London
          date_start: '2019-06-01'
          date_end: '2020-02-28'
          description: Taught courses in decision science and strategic decision making to cohorts of summer school graduates and management-executives at the department of Management.
        - title: Research and Teaching Assistant
          company: University of Manchester
          company_url: 'https://www.alliancembs.manchester.ac.uk/research/decision-and-cognitive-sciences-research-centre/'
          location: Booth Street, Manchester
          date_start: '2016-09-01'
          date_end: '2019-11-30'
          description: Supported faculty and student research projects and taught courses in critical theory, research methods and applied statistics at the Alliance Manchester Business School.
    design:
      columns: '2'
      
  
  - block: collection
    id: featured
    content:
      title: Featured Publications
      filters:
        folders:
          - publication
        featured_only: true
    design:
      columns: '2'
      view: card
  - block: collection
    content:
      title: Recent Publications
      text: |-
        {{% callout note %}}
        Quickly discover relevant content by [filtering publications](./publication/).
        {{% /callout %}}
      filters:
        folders:
          - publication
        exclude_featured: true
    design:
      columns: '2'
      view: citation
  - block: collection
    id: talks
    content:
      title: Recent & Upcoming Talks
      filters:
        folders:
          - event
    design:
      columns: '2'
      view: compact
  - block: tag_cloud
    content:
      title: Popular Topics
    design:
      columns: '2'
  
---
