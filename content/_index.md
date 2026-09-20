---
# Leave the homepage title empty to use the site title
title:
date: 2026-09-18
type: landing

sections:
  - block: hero
    content:
      title: Prairie Pathways
      text: |
        Documenting the history of agricultural landscape change — and celebrating the heritage of the rural Kansas communities living it.
      cta:
        url: ./participate/
        label: Share your story
        icon: microphone
        icon_pack: fas
      cta_alt:
        url: ./about/
        label: About the project
      cta_note:
        label: A community-centered research project, supported by the U.S. National Science Foundation.
    design:
      background:
        image:
          filename: hero.jpg
          filters:
            brightness: 0.5
          parallax: false
          position: center
          size: cover
        text_color_light: true
      spacing:
        padding: ['170px', '0', '150px', '0']

  - block: markdown
    content:
      title: Understanding how farming — and rural life — have changed
      subtitle: ''
      text: |
        Across Kansas, the crops grown in the field and the shape of rural communities have changed
        profoundly over the past century. **Prairie Pathways** is a community-centered research project
        working to understand *why* those changes happened and *how* the people who lived them
        make sense of them.

        We study the social, cultural, economic, ecological, and policy processes that have shaped
        farm types, crop diversity, and community life. Our aim is not to argue for any one way of
        farming, but to document these histories, learn from them, and return them to the communities
        they belong to.

        Alongside this research we gather **oral histories** and build **story maps** that celebrate the
        agricultural heritage of rural Kansas — the knowledge, decisions, and lived experience of
        farmers, community leaders, local historians, elders, and the organizations that support them.

        {{% cta cta_link="./about/" cta_text="Learn more about the project →" %}}
    design:
      columns: '1'

  - block: markdown
    content:
      title: Explore
      text: |
        <div class="row mt-4">
          <div class="col-md-4 mb-4">
            <div class="card h-100 shadow-sm border-0">
              <div class="card-body">
                <h3 class="card-title h4"><i class="fas fa-microphone-lines text-primary pr-2"></i> Oral Histories</h3>
                <p class="card-text">First-person accounts of agricultural and community change, recorded with the people who remember it.</p>
                <a class="stretched-link" href="./oral-histories/">Listen &amp; read →</a>
              </div>
            </div>
          </div>
          <div class="col-md-4 mb-4">
            <div class="card h-100 shadow-sm border-0">
              <div class="card-body">
                <h3 class="card-title h4"><i class="fas fa-map-location-dot text-primary pr-2"></i> Story Maps</h3>
                <p class="card-text">Interactive maps that trace how landscapes, livelihoods, and towns have shifted over time.</p>
                <a class="stretched-link" href="./storymaps/">Explore the maps →</a>
              </div>
            </div>
          </div>
          <div class="col-md-4 mb-4">
            <div class="card h-100 shadow-sm border-0">
              <div class="card-body">
                <h3 class="card-title h4"><i class="fas fa-handshake-angle text-primary pr-2"></i> Participate</h3>
                <p class="card-text">Farmers, elders, historians, and community leaders — we would be grateful to talk with you.</p>
                <a class="stretched-link" href="./participate/">Get involved →</a>
              </div>
            </div>
          </div>
        </div>
    design:
      columns: '1'
      spacing:
        padding: ['0', '0', '20px', '0']

  - block: collection
    content:
      title: Featured stories
      subtitle: ''
      text: 'A few of the histories and maps we are gathering. New material is added as the project grows.'
      count: 3
      filters:
        folders:
          - oral-histories
          - storymaps
        exclude_featured: false
      order: desc
    design:
      view: card
      columns: '2'

  - block: markdown
    content:
      title: Every farm has a story. We would love to hear yours.
      text: |
        If you farm, ranch, or have deep roots in a rural Kansas community — or if you help others who do —
        your memories and knowledge are part of this heritage. Sharing a story is voluntary, and you decide
        how your words and name are used.

        {{% cta cta_link="./participate/" cta_text="See how to take part →" %}}
    design:
      columns: '1'
      background:
        image:
          filename: heritage.jpg
          filters:
            brightness: 0.45
          parallax: false
          position: center
          size: cover
        text_color_light: true
      spacing:
        padding: ['90px', '0', '90px', '0']
      css_class: fullscreen

  - block: collection
    content:
      title: Latest news
      subtitle: ''
      text: ''
      count: 3
      filters:
        folders:
          - post
      order: desc
    design:
      view: card
      columns: '2'

  - block: markdown
    content:
      title:
      subtitle:
      text: |
        {{% cta cta_link="./people/" cta_text="Meet the team →" %}}
    design:
      columns: '1'
---
