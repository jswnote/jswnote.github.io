---
title: "C++"
permalink: /template/
author_profile: true
---

{% assign cpp_posts = site.categories["Template"] %}

{% for post in cpp_posts %}
## [{{ post.title }}]({{ post.url }})

{{ post.excerpt }}

{% endfor %}