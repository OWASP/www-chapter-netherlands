---

layout: col-sidebar
title: OWASP Netherlands
tags: netherlands
region: Europe
meetup-group: OWASP-Chapter-Netherlands-Meetup

---

{% include menu.md currentPage="pastevents" %} 

{% for year in site.data.events %}

{% year %}

{% endfor %}

{% assign events = site.data.events.2022 | sort: 'date' %}

{% for event in events %}

{{event.date | date: "%-d %B %Y"}}

{% endfor %}
