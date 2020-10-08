---
layout: default
title: Archive
---
{% assign pages = site.pages | sort: "date" %}
{% for page in pages %}
    {% if page.hidden == true %}
        {% continue %}
    {% endif %}
    {% assign skip = false %}
    {% for static in site.static_files %}
        {% if page.url == "/" or page.url == static.path %}
            {% assign skip = true %}
            {% break %}
        {% endif %}
    {% endfor %}
    {% if skip == true %}
        {% continue %}
    {% endif %}
[[{{ page.date | date: "%b %d, %Y" }}] [{% for tag in page.tags %}{{ tag }}{% unless forloop.last %}, {% endunless %}{% endfor %}] {{ page.title }}{% if page.subtitle %} ({{ page.subtitle }}){% endif %}]({{ page.url | relative_url }})
{% endfor %}
