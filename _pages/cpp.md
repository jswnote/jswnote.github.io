---
title: "C++"
permalink: /cpp/
author_profile: true
---

{% assign cpp_posts = site.categories["C++"] %}

{% for post in cpp_posts %}
## [{{ post.title }}]({{ post.url }})

{{ post.excerpt }}

{% endfor %}