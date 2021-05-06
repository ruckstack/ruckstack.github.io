---
layout: splash
author_profile: false
permalink: /
header:
  overlay_color: "#000"
  overlay_filter: "0.2"
  overlay_image: /assets/images/home-splash.jpg
  actions:
    - label: "Download"
      url: "/download"
excerpt: "Your entire stack + more...to go"
classes: wide
feature_row:
  - image_path: /assets/images/disk.jpg
    alt: "Built for ISVs"
    title: "Built for ISVs"
    excerpt: "Deploying your software in other people's environments is HARD.               
                Package and deploy your entire application stack from a single installable file.
                "
    url: "/isv"
    btn_class: "btn--primary"
    btn_label: "Learn more"
  - image_path: /assets/images/matrix.jpg
    alt: "Modern App Server"
    title: "Modern App Server"
    excerpt: "Focus on YOUR code without worrying about the surrounding infrastructure. Any technology, any services."
    url: "/modern-app-server"
    btn_class: "btn--primary"
    btn_label: "Learn more"
  - image_path: /assets/images/cargo.jpg
    alt: "Industry Standards"
    title: "Industry Standards"
    excerpt: "Built on battle-tested container and orchestration systems. Built-in best practices without the complexity."
    url: "/industry-standards"
    btn_class: "btn--primary"
    btn_label: "Learn more"      
---

{% include feature_row %}

<div style="column-count: 2">
<div>
<h1>Recent News</h1>

<dl>
{% for post in site.posts %}

  {% if forloop.index > 3 %}
    {% break %}
  {% endif %}

<dt><a href="{{ post.url }}">{{ post.title }}</a></dt>
<dl style="margin-left: 20px; margin-top: 5px">{{ post.excerpt }}</dl>

{% endfor %}

<dt><a href="/blog">Read More...</a></dt>
<dl style="margin-left: 20px; margin-top: 5px">See everything we've had to say</dl>

</dl>
</div>

<div>
<h1>Demo</h1>
<div style="border: 1px solid #EAEAEA;">
{% include video id="RAvWIUZblRM" provider="youtube" %}
</div>
</div>

</div>
