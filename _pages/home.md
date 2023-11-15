---
layout: splash
permalink: /
hidden: true
header:
  overlay_color: "#000"
  overlay_filter: "0.8"
  overlay_image: /assets/images/website-main-banner.png

excerpt: My personal website, portfolio, and blog.

feature_row:
  - title: "Blog Posts By Year"
    excerpt: "All posts sorted by year"
    url: "/year-archive/"
    btn_class: "btn--primary"
    btn_label: "Read blog"

  - title: "Portfolio"
    excerpt: "A formal list of projects I've worked on with links to more detailed posts for each."
    url: "/about/"
    btn_class: "btn--primary"
    btn_label: "Learn more"

  - title: "Play my games"
    excerpt: "All of my games are hosted on Itch IO. I also feature a few collections of other people's projects I find interesting or possibly useful."
    url: "https://queenofsquiggles.itch.io/"
    btn_class: "btn--primary"
    btn_label: "Play!"      
    # Properties to add an image background
    # image_path: /assets/images/mm-free-feature.png
    # alt: ""
  - title: "See my article backlog"
    excerpt: "A list of potential article ideas that I want to do eventually..."
    url: /backlog/
    btn_class: "btn--primary"
    btn_label: "See Backlog"

---

{% include feature_row %}

{% assign entries_layout = page.entries_layout | default: 'list' %}

{% assign postsByYear = site.posts | where_exp: "item", "item.hidden != true" | group_by_exp: 'post', 'post.date | date: "%Y"' %}
{% for year in postsByYear %}
  <section id="{{ year.name }}" class="taxonomy__section">
    <h2 class="archive__subtitle">{{ year.name }}</h2>
    <div class="entries-{{ entries_layout }}">
      {% for post in year.items %}
        {% include archive-single.html type=entries_layout %}
      {% endfor %}
    </div>
    <a href="#page-title" class="back-to-top">{{ site.data.ui-text[site.locale].back_to_top | default: 'Back to Top' }} &uarr;</a>
  </section>
{% endfor %}

<!--I want my website verified on my mastodon, but I'd really prefer the link isn't prominent unless I can style it better-->
<a hidden rel="me" href="https://blobfox.coffee/@queenofsquiggles">Mastodon</a>
