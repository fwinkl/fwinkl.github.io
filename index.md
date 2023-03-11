---
layout: default
---

{% for page in site.scig %}
  <h5>
    <i class="bi bi-calendar-event"></i> {{ page.date | date: "%a %d %b %Y" }} <a href="{{ page.url }}">{{ page.title }}</a>
  </h5>
  <p>{{ page.excerpt | markdownify }}</p>
  <p><b>{{ page.rating }}</b>: {% include hikestats.html %}</p>
{% endfor %}
