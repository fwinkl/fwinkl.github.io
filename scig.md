---
layout: default
---

<h1>My SCIG hikes</h1>
I am organizing the following ski club hikes this year.
For a list of all SCIG hikes see the <a href="https://www.scig.ch/randonnees-pedestres">official SCIG website</a>.

{% for page in site.scig %}
  <h5>
    <i class="bi bi-calendar-event"></i> {{ page.date | date: "%a %d %b %Y" }} <a href="{{ page.url }}">{{ page.title }}</a>
  </h5>
  <p>{{ page.excerpt | markdownify }}</p>
  <p><b>{{ page.rating }}</b>: {% include hikestats.html %}</p>
{% endfor %}
