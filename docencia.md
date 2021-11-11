---
layout: single
title: Publicaciones directorio /docencia
permalink: /docencia
toc: true
---

{% for post in site.categories ["docencia"] %}
* [{{post.title}}]({{post.url}})
{% endfor %}