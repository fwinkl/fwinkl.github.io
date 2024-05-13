---
title: My SCIG hikes
layout: default
---

<h1>My SCIG hikes</h1>
I am organizing the following ski club hikes this year.
For a list of all SCIG hikes see the <a href="https://www.scig.ch/randonnees-pedestres">official SCIG website</a>.

{% capture now %}{{"now" | date: "%s"}}{% endcapture %}
{% assign hikes = site.scig | sort: "date" | reverse %}
{% for page in hikes %}
    {% if page.draft %}
        {% continue %}
    {% endif %}
    {% capture hikedate %}{{page.date | date: "%s"}}{% endcapture %}
    {% if hikedate < now -%}
        {% assign style = "old" %}
    {% endif %}
    {% capture hikeyear %}{{page.date | date: "%Y"}}{% endcapture %}
    {% if year != hikeyear %}
        {% assign year = hikeyear %}
<h4 class="year {{ style }}">{{ hikeyear }}</h4>
    {% endif %}
<div class="row mb-2 {{ style }}">
    <h5><i class="bi bi-calendar-event"></i>&nbsp;{{ page.date | date: "%a %d %b %Y" }}&nbsp;&nbsp;<a href="{{ page.url }}">{{ page.title }}</a></h5>
    <div class="col-sm-3">
        <a href="{{ page.url }}"><img src="{{ page.media[0].url }}" class="img-fluid {{ style }}"></a>
    </div>
    <div class="col-sm">
        {{ page.excerpt | markdownify }}
        <b>{{ page.rating }}</b>: {% include hikestats.html %}
            <i class="bi bi-newspaper"></i>&nbsp;<a href="{{ page.url }}">Description</a>
    </div>
</div>
{% endfor %}
