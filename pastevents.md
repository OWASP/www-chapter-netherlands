---

layout: col-sidebar
title: OWASP Netherlands
tags: netherlands
region: Europe
meetup-group: OWASP-Chapter-Netherlands-Meetup

---

{% include menu.md currentPage="pastevents" %} 

{% assign years = site.data.events | sort %}

{% for year_hash in years  %}

{% assign year = year_hash[0] %}

{{ year }}

{% endfor %}

{% assign events = site.data.events.2022 | sort: 'date' %}

{% for event in events %}

{{event.date | date: "%-d %B %Y"}}

{% endfor %}
